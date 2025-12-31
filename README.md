### Overview

The [.NET MAUI Navigation Drawer](https://www.syncfusion.com/maui-controls/maui-navigationdrawer) allows users to open the drawer programmatically on multiple sides with different toggle methods. The multiple drawers can be implemented using the following drawer settings.

 * [DrawerSettings](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_DrawerSettings)
 * [SecondaryDrawerSettings](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_SecondaryDrawerSettings) 

 Opening drawers programmatically provides full control over the navigation experience without relying on swipe gestures. This approach is beneficial in the following scenarios:

* Triggering navigation from specific UI elements like buttons, icons, or menu actions.
* Opening or closing drawers based on application logic, for example, after a successful login, when displaying contextual options, or during workflow transitions.

This article explains how to open the drawer programmatically in the .NET MAUI Navigation drawer. 
 
To open the drawers programmatically in the Navigation Drawer, follow these steps:
 
1. Add a Navigation Drawer and include the  [DrawerSettings](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_DrawerSettings) for the primary drawer, and [SecondaryDrawerSettings](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_SecondaryDrawerSettings) for the secondary drawer.
2. Attach button click events to call the [ToggleDrawer](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_ToggleDrawer) method for the primary drawer and [ToggleSecondaryDrawer](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.SfNavigationDrawer.html#Syncfusion_Maui_NavigationDrawer_SfNavigationDrawer_ToggleSecondaryDrawer) method for the secondary drawer. These methods allow the drawers to be opened or closed programmatically when the corresponding button is clicked.
3. Alternatively, the [IsOpen](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.NavigationDrawer.DrawerSettings.html#Syncfusion_Maui_NavigationDrawer_DrawerSettings_IsOpen) property can be used to open or close the drawer programmatically by setting its value to true or false. This provides a direct way to control the drawer state without invoking the toggle methods.

**MainPage.xaml**
 
```
<navigationDrawer:SfNavigationDrawer x:Name="navigationDrawer">
    <navigationDrawer:SfNavigationDrawer.ContentView>
        <Grid RowDefinitions="80, *">
            <Grid BackgroundColor="#6750A4" ColumnDefinitions="*, *">
                <Button Text="&#xe719;" Clicked="OnPrimaryDrawerToggled" FontFamily="MauiMaterialAssets" FontAttributes="Bold" TextColor="White" FontSize="24" BackgroundColor="Transparent" HorizontalOptions="Start" Grid.Column="0" />
                <Button Text="&#xe716;" Clicked="OnSecondaryDrawerToggled" FontFamily="MauiMaterialAssets" FontAttributes="Bold" TextColor="White" FontSize="24" BackgroundColor="Transparent" HorizontalOptions="End" Grid.Column="1" />
            </Grid>
            <Label Grid.Row="1" Text="Main Content" HorizontalOptions="Center" VerticalOptions="Center" HorizontalTextAlignment="Center" Margin="16" />
        </Grid>
    </navigationDrawer:SfNavigationDrawer.ContentView>

    <!-- Primary drawer settings -->
    <navigationDrawer:SfNavigationDrawer.DrawerSettings>
        <navigationDrawer:DrawerSettings x:Name="primaryDrawer" Position="Left" DrawerWidth="300" EnableSwipeGesture="True" Transition="SlideOnTop">
            <navigationDrawer:DrawerSettings.DrawerContentView>
                    <VerticalStackLayout Padding="12" Spacing="2">
                        <Label Text="Mail" FontAttributes="Bold" FontSize="18" VerticalTextAlignment="Center" HorizontalTextAlignment="Center" Margin="12, 0" />
                        <Label Text="Inbox" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Drafts" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Sent" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Starred" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Spam" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Trash" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                    </VerticalStackLayout>
            </navigationDrawer:DrawerSettings.DrawerContentView>
        </navigationDrawer:DrawerSettings>
    </navigationDrawer:SfNavigationDrawer.DrawerSettings>

    <!-- Secondary drawer settings -->
    <navigationDrawer:SfNavigationDrawer.SecondaryDrawerSettings>
        <navigationDrawer:DrawerSettings x:Name="secondaryDrawer" Position="Right" DrawerWidth="300" EnableSwipeGesture="True" Transition="SlideOnTop">
            <navigationDrawer:DrawerSettings.DrawerContentView>
                    <VerticalStackLayout Padding="12" Spacing="2">
                        <Label Text="Settings" FontAttributes="Bold" FontSize="18" VerticalTextAlignment="Center" HorizontalTextAlignment="Center" Margin="12, 0" />
                        <Label Text="Preferences" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Filters" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="Help" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                        <Label Text="About" Padding="12,14" VerticalTextAlignment="Center" FontSize="15" />
                    </VerticalStackLayout>
            </navigationDrawer:DrawerSettings.DrawerContentView>
        </navigationDrawer:DrawerSettings>
    </navigationDrawer:SfNavigationDrawer.SecondaryDrawerSettings>
</navigationDrawer:SfNavigationDrawer>
```
 
**MainPage.xaml.cs**

```
private void OnPrimaryDrawerToggled(object sender, EventArgs e)
{
    navigationDrawer.ToggleDrawer();
    // primaryDrawer.IsOpen = true;
}

private void OnSecondaryDrawerToggled(object sender, EventArgs e)
{
    navigationDrawer.ToggleSecondaryDrawer();
    // secondaryDrawer.IsOpen = true;
}
```

**Output**
  
 ![programmaticdrawer-kb2.gif](https://support.syncfusion.com/kb/agent/attachment/article/22318/inline?token=eyJhbGciOiJodHRwOi8vd3d3LnczLm9yZy8yMDAxLzA0L3htbGRzaWctbW9yZSNobWFjLXNoYTI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6IjU2NzQ5Iiwib3JnaWQiOiIzIiwiaXNzIjoic3VwcG9ydC5zeW5jZnVzaW9uLmNvbSJ9.WIaHrJ0zEfRHPokGKOQ99TZ72MForlz_WltnfbpxlhQ)