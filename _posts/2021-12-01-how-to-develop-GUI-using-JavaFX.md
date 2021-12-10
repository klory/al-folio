---
layout: post
title: How to develop GUI on desktop using JavaFX
# description: 
date: 2021-12-01
comments: true
---


[JavaFX](https://openjfx.io/) (API is [here](https://docs.oracle.com/javase/8/javafx/api/overview-summary.html)) is used to design GUI on desktop ([first released](https://en.wikipedia.org/wiki/JavaFX) in Dec 2008), mobile and embeded systems (Raspberry Pi?). The current long-term-support version is [JavaFX17](https://gluonhq.com/products/javafx/) (the one I used). This post is for desktop. Developing softwares are not easy, but they follow certain patterns, knowing the patterns can speed up the development. 

**These are all based on my understanding so let me know if there are mistakes and I will fix them.**

<div class='row mt-3'>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/2021-12-01-how-to-develop-GUI-using-JavaFX/2021-12-01-16-14-24.png" data-zoomable>
    </div>
</div>

Of course, you also need JAVA installed(at least Java 8). Recent Java SDK already contains JavaFX, but it's not bad to try latest features in new JavaFX release. My configuration:

* MacOS Catalina
* Eclipse 2021-09 
* Java 14
* JavaFX 17

# Before you start
* Install e(fx)clipse from Eclipse Marketplace to speed up the development.
* Download SceneBuilder from [here](https://gluonhq.com/products/scene-builder/). We can use it to design GUI by simply dragging the components instead of writing every line of code. (similar to the `Design` view for `*.xml` in Android Studio or `Canvas` view in Xcode)
* In Eclipse Preferences has one section for JavaFX, you can specify SceneBuilder executable location as well as JavaFX classpath and other options.

## Debugging using Alert
```java
Alert alert = new Alert(AlertType.ERROR);
alert.setTitle("Error");
alert.setHeaderText("your header");
alert.setContentText("your content");
alert.showAndWait();
```

# All programs starts from Main
GUI app is not like an app in Terminal. An app in terminal accepts input and prints the output, quite often it only runs once and exits.

GUI app needs to keep the window open and waits for users to interact with it. To keep the window open, GUI apps need to keep an event loop running, think of it as a function which is called repeatedly and quickly to draw the window on screen. This is usually handle by the framework, in JavaFX, it means calling `launch(args)` in your main function.

```java
public static void main(String[] args) {
    launch(args);
}
```

In Android(Android Studio) or iOS(XCode) development, similar function is implicitly called (you may not even see the main function at all).

# [First window](#first-window)

JavaFX uses `start()` (`onCreate()` for Android) to mark the start of the event loop. It is the place where you load your datas and display your startup window. Like other GUI frameworks, JavaFX can load window from configuration file (`*.fxml` files for JavaFX), these XML files can also be directly modified using SceneBuilder, after you install e(fx)clipse, just write click on the fxml file and 'OpenInSceneBuilder'.

```java
public void start(Stage primaryStage) {
    // handle data loading locally or remotely
    // ...

    // display startup window
    AnchorPane root = FXMLLoader.load(getClass().getResource("startup-window.fxml"));
    // or
    // Parent root = FXMLLoader.load(getClass().getResource("startup-window.fxml"));
    // or 
    // FXMLLoader fxmlLoader = new FXMLLoader();
    // fxmlLoader.setLocation(getClass().getResource("startup-window.fxml"));
    // AnchorPane root = fxmlLoader.load();

    // do stuffs with loginController, e.g. reuse the window
    LoginController loginController = loader.getController();
    loginController.setStage(primaryStage); // reuse the window
    
    // show the scene (i.e., content)
    Scene scene = new Scene(root);
    primaryStage.setResizable(false);
    primaryStage.setScene(scene);
    primaryStage.show();
}
```

## Procedure
* Load root pane from `fxml` file.
* Create scene from root pane.
* Set scene to stage and show stage.

## Keys
* One `fxml` to one controller is the easiest way to organize the project.

Bonus: do something before quitting the app.
```java
primaryStage.setOnCloseRequest(event -> {
    // handle data saving locally or remotely
    // ...
    System.exit(0);
});
```

# Transitions to other windows
A stage corresponds to one window, so whenever you create a new stage, a new window will open. You can also reuse the same stage by passing it to other controllers, see [First Window](#first-window).

* Stage: a window
* Scene: the content in the window

```java
// Step 1. acquire the stage
// create new stage
Stage stage = new Stage();
// or use current stage, see [First Window] section

// Step 2. transit
XMLLoader fxmlLoader = new FXMLLoader();
fxmlLoader.setLocation(getClass().getResource("startup-window.fxml"));
AnchorPane root = fxmlLoader.load();
stage.setScene(new Scene(root));
stage.setResizable(false);
stage.show();
```

# Commmon Layout
Usually a program is a combination of only a few layouts:
* Table View
* Tile View
* Tab View

<div class='row mt-3'>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/2021-12-01-how-to-develop-GUI-using-JavaFX/2021-12-10-11-58-02.png" data-zoomable>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/2021-12-01-how-to-develop-GUI-using-JavaFX/2021-12-10-11-38-00.png" data-zoomable>
    </div>
    <div class="col-sm mt-3 mt-md-0">
        <img class="img-fluid rounded z-depth-1" src="{{ site.baseurl }}/assets/img/2021-12-01-how-to-develop-GUI-using-JavaFX/2021-12-10-11-56-29.png" data-zoomable>
    </div>
</div>

To combine them together, you need a few layouts that give you the freedom to do it:
* AnchorPane
* SplitPane
* GridPane
* ...

And a program usually uses only a few kind of controls, there are otheres, but usually it's just some similar things based on these:
* Button
* Label
* Checkbox
* DataPicker
* ProgressBar
* TextField or TextArea (depends on whether you need input one line or mutiple lines)
* ImageView
* VideoView
* WebView

These standard things are defined in every UI framework, in JavaFX is would be [javafx.scene.layout](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/layout/package-summary.html) and [javafx.scene.control](https://docs.oracle.com/javase/8/javafx/api/javafx/scene/control/package-summary.html).

## ListView
ListView let you display a list of items.
1. Add a ListView control `listView` in your FXML file (e.g. use SceneBuilder).
2. Add `fx:id` to the ListView.
3. In the controller class:


```java
// Assume User class is defined
// Get data (local/remote) and save it into an `ObservableList<Object> list`.
userList = get_data(); // ObservableList<User>

// set content of each row
listView.setItems(userList); //set items
// find exactly which string to show for the item
userList.setCellFactory(new Callback<ListView<User>, ListCell<User>>() {
    @Override
    public ListCell<User> call(ListView<User> userListView) {
        return new ListCell<User>() {
            @Override
            protected void updateItem(User item, boolean empty) {
                super.updateItem(item, empty);
                if (item != null) {
                    setText(item.getUserName()); // find the property in User class to show
                } else {
                    setText(null);
                }
            }
        };
    }
});
listView.getSelectionModel().select(0); // select the first item

// click one row
userList.getSelectionModel().selectedItemProperty().addListener(
    (observable, value1, value2) -> {
        if (value2 != null) {
            userName.setText(value2.getUserName());
        } else {
            userName.setText(null);
        }
    }
);

// get selected item
User selectedUser = listView.getSelectionModel().getSelectedItem();
```

## TabPane

## TilePane