---
layout: page
title : What's New in 1.7 RC3
group: Getting Started
weight: 3

---

We are very proud to announce the **final experimental build** of **Awesomium.NET 1.7**, we think you'll be pretty impressed with all the new features and enhancements we've added these past few months.

* [Download the Awesomium 1.7 RC3 SDK (Includes Awesomium.NET binaries and samples)](http://www.awesomium.com/download)
* [Awesomium.NET 1.7 RC3 API Reference](http://www.awesomium.com/docs/1_7_rc3/sharp_api)
* [Setting up on Windows](http://wiki.awesomium.net/getting-started/setting-up-on-windows.html)

A lot has gone into this release. Before you go through the changes in Awesomium.NET, take a look at the major changes in native Awesomium:

* [Awesomium 1.7 Final Candidate](http://forums.awesomium.com/viewtopic.php?f=3&t=86)

Here is a quick summary of the big changes in **Awesomium.NET**:

### New Features

* Added support for the new, *windowed* web-views that render directly to `HWND`. Read more in [Introduction to Web-Views](introduction-to-web-views.html).
* Added the **Windows Forms [`WebControl`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Forms_WebControl)**. The control now wraps a *windowed* web-view.
* Added [`IResourceInterceptor`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_IResourceInterceptor). You can assign your implementation to the `WebCore` to intercept requests for resources, modify requests, and return custom responses. See an example of usage, in the included **JavascriptSample**.
* Added the [`IWebViewPresenter`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Controls_IWebViewPresenter) interface to the *Awesomium.Windows.Controls* assembly, for creating custom presenters of an `IWebView` instance, that can be added to the style of the `WebControl`.
* The **WPF `WebControl`** can now wrap a *windowed* web-view. A predefined presenter has been added (see [`WebViewHost`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Controls_WebViewHost)), that is used to present a *windowed* web-view, taking advantage of full hardware acceleration. Read more in: [Working with Windowed Web-Views](working-with-windowed-web-views.html).
* The WPF and Windows Forms WebControls, now handle downloads and selecting local files automatically, by showing the necessary dialogs. Custom handling is still in place and improved. Read more about custom handling, here: [`FileDialogEventArgs.Handled`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_FileDialogEventArgs_Handled).
* Significantly improved the powerful [`DataSource`]() API that allows you to provide a custom resource loader for a set of URLs that match a certain prefix. See the **API Changes** section below, and read the [Using Data-Sources](using-data-sources.html) article. All predefined DataSources are now under the new *Awesomium.Core.Data* namespace.
* Added [`DirectoryDataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_DirectoryDataSource), a predefined `DataSource` that loads resources from a local directory. Resources can also be cached in-memory for fast response.
* Added [`ResourceDataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_ResourceDataSource), a predefined `DataSource` that loads resources from embedded or packed (Build Action: Resource) application resources. The `ResourceDataSource` can also load resources from an external managed assembly.
* Added the base [`DataSourceProvider`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Data_DataSourceProvider), a WPF `DataSource` provider that can be used in XAML.
* Added WPF DataSourceProviders under the new [`Awesomium.Windows.Data`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=N_Awesomium_Windows_Data) namespace, for each of the available DataSources under *Awesomium.Core.Data*. These can be used in XAML (see [Using Data-Sources](using-data-sources.html)).
* Added the ability to specify one ore more [`DataSourceProvider`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Data_DataSourceProvider) instances to a `WebSessionProvider` in XAML (see the **API Changes** section below).
* The WPF `WebSessionProvider` can now provide a `WebSession` that is synchronized to disk.
* The Windows Forms `WebControl` and the `WebView`, now support Data Binding. For more details, read the **Handling Events - Binding to Notifications** section in [Introduction to Web-Views](introduction-to-web-views.html#notifications).
* Added the [`IWebViewIMEComposition`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_IWebViewIMEComposition) service for showing your own **I**nput **M**ethod **E**ditor widget into **offscreen** web-views (useful for input of Asian languages). For more details, read the **Features as a Service** section in [Introduction to Web-Views](introduction-to-web-views.html).


### API Changes

#### New API:

##### *Awesomium.Core*

* [`WebCore.ResourceInterceptor`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_WebCore_ResourceInterceptor): Allows you to specify your [`IResourceInterceptor`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_IResourceInterceptor) implementation.
* [`WebConfig.AdditionalOptions`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_WebConfig_AdditionalOptions): Gets or sets additional command-line options for Chromium.
* [`WebPreferences.EnableGPUAcceleration`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_WebPreferences_EnableGPUAcceleration): Gets or sets if GPU accelerated compositing (experimental) should be enabled. This is only compatible with *windowed* `IWebView` instances at this time (see [Introduction to Web-Views](introduction-to-web-views.html)).
* [`WebSession.SetCookie`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_WebSession_SetCookie): Sets a cookie for a certain URL asynchronously.
* [`WebSession.GetDataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_WebSession_GetDataSource): Gets the `DataSource` previously registered for an asset host, if any.
* [`WebSession.DataSources`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_WebSession_DataSources): Gets a list of DataSources that have been registered with the `WebSession`.
* [`Utilities.GetMimeType`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Utilities_GetMimeType): Gets the mime type for a specified file name, based on its extension.
* [`Utilities.ToUri`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Utilities_ToUri): Gets a `Uri` instance from a well formatted URI string.
* [`IWebView.Download`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=E_Awesomium_Core_IWebView_Download): Occurs when the page requests to begin downloading a certain file. Technology specific WebControls, will display a dialog.
* [`IWebView.DownloadComplete`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=E_Awesomium_Core_IWebView_DownloadComplete): Occurs when a download is finished.
* [`IWebView.DownloadProgress`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=E_Awesomium_Core_IWebView_DownloadProgress): Occurs when the progress of a download is updated.
* [`IWebView.NativeWindow`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_NativeWindow): Gets the actual window handle that was created by a `IWebView` instance. This is only valid for *windowed* `IWebView` instances (see [Introduction to Web-Views](introduction-to-web-views.html)).
* [`IWebView.ParentView`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_ParentView): Gets the parent view (if any) of an `IWebView` instance (see [Handling Child Web-Views](handling-child-web-views.html)).
* [`IWebView.ParentWindow`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_ParentWindow): Gets or sets the parent window for a `IWebView` instance. This is only valid for *windowed* `IWebView` instances (see [Introduction to Web-Views](introduction-to-web-views.html)). **WebControls handle this internally.**
* [`IWebView.ProcessHandle`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_ProcessHandle): Get the handle for the corresponding child-process hosting a `IWebView` instance.
* [`IWebView.ProcessID`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_ProcessID): Get the unique ID for the corresponding child-process hosting a `IWebView` instance.
* [`IWebView.TerminationStatus`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_TerminationStatus): Gets the termination status of a `IWebView` instance.
* [`IWebView.ViewType`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_ViewType): Gets the [type](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_WebViewType) of a `IWebView` instance. This is implemented as read-write in the WPF `WebControl`.
* [`DataSource.AssetHosts`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_Data_DataSource_AssetHosts): Gets a list of asset hosts, a `DataSource` has been registered to handle, in a `WebSession`.
* [`DataSource.WebSession`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_Data_DataSource_WebSession): Gets the `WebSession` a `DataSource` has been added to.
* [`AsyncDataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_AsyncDataSource): Represents a base `DataSource` that loads resources asynchronously. The new [`DirectoryDataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_DirectoryDataSource) and [`ResourceDataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_ResourceDataSource) DataSources, inherit this class. See **New Features** above.
* [`DataSourceRequest`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_DataSourceRequest): Represents a request for a resource.
* [`DataSourceResponse`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_DataSourceResponse): Represents the response to a `DataSourceRequest`.

##### *Awesomium.Windows.Controls* (WPF)

* [`WebViewHost`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Controls_WebViewHost): Represents a WPF presenter of a *windowed* `IWebView` instance (read about `IWebViewPresenter` in the **New Features** above. Also read: [Introduction to Web-Views](introduction-to-web-views.html)).
* [`WebControl.ViewType`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Windows_Controls_WebControl_ViewType): Allows you to set the [type](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_WebViewType) of the underlying `IWebView`.
* [`WebSessionProvider.DataPath`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Windows_Controls_WebSessionProvider_DataPath): Gets or sets the disk data path of this session, if any.
* [`WebSessionProvider.DataSources`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Windows_Controls_WebSessionProvider_DataSources): Gets a collection of pairs of asset hosts and `DataSourceProvider` instances.
* [`DataSourceProvider`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Data_DataSourceProvider): Represents the base class for WPF `DataSource` providers (see `Awesomium.Windows.Data` below).
* [`Awesomium.Windows.Data`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=N_Awesomium_Windows_Data): This new namespace includes predefined WPF `DataSource` providers for each available `DataSource` under [`Awesomium.Core.Data`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=N_Awesomium_Core_Data), that can be used in XAML (see [Using Data-Sources](using-data-sources.html)).

##### *Awesomium.Windows.Forms* (Windows Forms)

* [`WebControl`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Forms_WebControl): The Windows Forms `WebControl` is back! It now wraps a *windowed* web-view by default.
* [`AddressBox`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Forms_AddressBox): Represents a Windows Forms TextBox that behaves as an address-box.
* [`ToolStripAddressBox`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Windows_Forms_ToolStripAddressBox): Represents a text box in a ToolStrip that behaves as an address-box.

#### Modified API

* `LoadURL` is deprecated and it will be removed in later releases of **Awesomium.NET**. Use the [`Source`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_IWebView_Source) property to load content to an `IWebView` instance.
* The base [`DataSource`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_DataSource) and all predefined managed DataSources have been moved under the [`Awesomium.Core.Data`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=N_Awesomium_Core_Data) namespace.
* [`DataSource.OnRequest`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Data_DataSource_OnRequest) now provides a [`DataSourceRequest`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_Data_DataSourceRequest) structure.
* [`SendResponse(Int32, UInt32, IntPtr, String)`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Data_DataSource_SendResponse_1) is deprecated. You should now use the new [`SendResponse(DataSourceRequest, DataSourceResponse)`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Data_DataSource_SendResponse).
* [`SendRequestFailed(Int32)`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Data_DataSource_SendRequestFailed_1) is deprecated. You should now use the new [`SendRequestFailed(DataSourceRequest)`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_Data_DataSource_SendRequestFailed).
* Two overloaded [`WebCore.CreateWebView`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=Overload_Awesomium_Core_WebCore_CreateWebView) have been added that accept a parameter that specifies the [type](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_WebViewType) of `WebView` to create (*offscreen* or *windowed*). Read [Using the WebView](using-the-webview.html).
* [`IWebView.PrintToFile`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_IWebView_PrintToFile) accepts the *outputDirectory* as a separate parameter.
* The [`WebKeyboardEvent`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_WebKeyboardEvent) is now a structure.


### <a id="bug-fixes"></a>Bug Fixes

* Fixed issue with `GC.Collect()` called too often by the internal `WebURLMarshaler`.
* Fixed issues with setting `IsTransparent`.
* Fixed exception that occurred when trying to use [`IWebView.PrintToFile`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=M_Awesomium_Core_IWebView_PrintToFile) (see the modified API above).
* Fixed exceptions that occurred when handling [`IWebView.ShowPopupMenu`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=E_Awesomium_Core_IWebView_ShowPopupMenu) and accessing [`WebPopupMenuInfo.Bounds`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_WebPopupMenuInfo_Bounds)
* Fixed bug that did now allow you to select content using the keyboard in the WPF `WebControl`.
* Fixed bug with keyboard modifiers not being applied to mouse and touch events in *offscreen* views (like the WPF `WebControl`).
* Fixed issues with commands not working in the WPF context menu.


Please [read here](http://forums.awesomium.com/viewtopic.php?f=3&t=86), the list of bugs fixed in native Awesomium. Some of them affected Awesomium.NET.


### <a id="known-issues"></a>Known Issues

* On **Windows 8**, applications that use *windowed* `IWebView` instances (such as the Windows Forms `WebControl`) and create **popup** child views (see [`ShowCreatedWebViewEventArgs.IsPopup`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_ShowCreatedWebViewEventArgs_IsPopup)), may crash when the application exits.
* On **Windows 8**, **WebGL** is currently not supported.

#### Under production:

* When you are using the **WPF `WebControl`**, [`SelectLocalFiles`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=E_Awesomium_Core_IWebView_SelectLocalFiles) events with [`FileDialogEventArgs.Mode`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=P_Awesomium_Core_FileDialogEventArgs_Mode) of [`WebFileChooserMode.OpenFolder`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=T_Awesomium_Core_WebFileChooserMode), will not display a dialog automatically. Currently, you will have to handle such events yourself.
* When you are using the WPF or Windows Forms WebControls, drop-down (popup) menus (e.g., HTML: `<select>`), are not displayed automatically. This feature will be added on the final release of v1.7. However, the new powerful API allows you to design and display these yourself, by handling the [`ShowPopupMenu`](http://awesomium.com/docs/1_7_rc3/sharp_api/?tc=E_Awesomium_Core_IWebView_ShowPopupMenu) event.