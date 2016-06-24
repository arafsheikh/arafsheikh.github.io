---
layout: post
title: "Eclipse Plug-in: Dynamic menu with click listener"
date: 2016-06-24 14:00:00
category: gsoc16
---

I'm writing an [Eclipse plug-in for coala](http://sheikharaf.me/gsoc16/gsoc-16-with-coala.html)
and recently I had to add a list of available
bears so that the user can choose the bear to use for code analysis.

I struggled for a
few days, experimenting different approaches. In this post I'll share the method that
I finally settled for.

First you have to add a dynamic `menuContribution` item to the `org.eclipse.ui.menus`
extension point. So your `plugin.xml` should look like this:

```xml
<extension
        point="org.eclipse.ui.menus">
    <menuContribution
        locationURI="popup:org.eclipse.ui.navigator.ProjectExplorer#PopupMenu?after=additions">
        <menu
            label="Run coala with">
            <dynamic
                class="com.coala.core.menu.BearMenu"
                id="com.coala.core.menu.bearListValues">
            </dynamic>
        </menu>
    </menuContribution>
</extension>
```

The `class` field points to the Java class the populates the dynamic `menuContribution` item.
This class should extend `org.eclipse.jface.action.ContributionItem`. 
So let's implement this class. The code looks like the following:

```java
public class BearMenu extends ContributionItem {

  public BearMenu() {
  }

  public BearMenu(String id) {
    super(id);
  }

  @Override
  public void fill(Menu menu, int index) {
    String[] bears = getBears();

    for (final String bear : bears) {
      MenuItem menuItem = new MenuItem(menu, SWT.CHECK, index);
      menuItem.setText(bear);
      menuItem.addSelectionListener(new SelectionAdapter() {
        public void widgetSelected(SelectionEvent event) {
          System.out.println("You clicked " + bear);
          // Analyze with coala here.
        }
      });
    }
  }

  private String[] getBears() {
    // returns an array containing names of bears
  }
```

This way you can dynamically add items to the menu and assign them click listeners.

There are other approaches as well, e.g.
[a dynamic menu with a corresponding handler](http://stackoverflow.com/questions/6876033/eclipse-plugin-creating-a-dynamic-menu-and-corresponding-handler), etc.
but I find this approach to be the easiest.
