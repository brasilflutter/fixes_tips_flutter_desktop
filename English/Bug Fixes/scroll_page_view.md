# Adding ScrollConfiguration to Use PageView in Flutter Desktop


* In Flutter, PageView is a widget widely used to create paged navigation interfaces. However, there is an important difference between the mobile and desktop versions of Flutter when it comes to scrolling behavior.

* For Mobile Applications
On mobile devices, PageView works perfectly without additional scrolling configurations, as the default scrolling behavior is already optimized for touch and drag.

* For Desktop Applications
In desktop environments, it is necessary to add an extra configuration to ensure that PageView works correctly with different input devices, such as mouse and touchpad. This is done using the ScrollConfiguration widget.

* Step by Step to Configure PageView in Flutter Desktop
Here is a tutorial on how to add ScrollConfiguration so that PageView works correctly in desktop applications:

  - Open your Flutter project and locate the file where you want to add PageView.
  
  - Add the ScrollConfiguration widget around your PageView to define the scrolling behavior.
  
  - Configure the scrolling behavior to accept input from devices such as touch and mouse.
  
  - Here is a complete example of how to do this:


```
class PageViewExample extends StatelessWidget {
  final PageController pageController = PageController();

  @override
  Widget build(BuildContext context) {
    return ScrollConfiguration(
      behavior: ScrollConfiguration.of(context).copyWith(
        dragDevices: {
          PointerDeviceKind.touch,
          PointerDeviceKind.mouse,
        },
      ),
      child: PageView(
        controller: pageController,
        scrollDirection: Axis.horizontal,
        children: [
          Container(
            height: 200,
            width: 200,
            color: Colors.blue,
            child: Center(
              child: Text('1', style: TextStyle(color: Colors.white, fontSize: 24)),
            ),
          ),
          Container(
            height: 200,
            width: 200,
            color: Colors.red,
            child: Center(
              child: Text('2', style: TextStyle(color: Colors.white, fontSize: 24)),
            ),
          ),
          Container(
            height: 200,
            width: 200,
            color: Colors.grey,
            child: Center(
              child: Text('3', style: TextStyle(color: Colors.white, fontSize: 24)),
            ),
          ),
        ],
      ),
    );
  }
}
```

* Explanation:
- ScrollConfiguration: Wraps PageView to customize scrolling behavior.
- behavior: Uses the context's default scrolling configuration (ScrollConfiguration.of(context)) and modifies the list of input devices (dragDevices), allowing touch and mouse.
- PageView: Defines the page control and the pages displayed.
- With this configuration, your PageView should work smoothly and responsively on both touch devices and desktop input devices such as mouse.