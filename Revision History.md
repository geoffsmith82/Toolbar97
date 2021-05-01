||
|**Toolbar97**
 **Revision History**|

**1.9** (5/01/21)

-   Added package for Delphi Sydney.
-   Added support for Win64.

**1.8** (2/23/04)

-   Toolbar97 is now **open source**. See the updated License.txt file for the license terms. (It's the [zlib license](http://www.opensource.org/licenses/zlib-license.php).)
-   Added package for Delphi 7.

**1.78a** (5/12/02)

-   Added C++Builder 6 support. Use the new *TB97\_cb6* package for C++Builder 6.

**1.78** (6/18/01)

-   Added Delphi 6 support. Use the new *TB97\_d6* package for Delphi 6.
-   *Fix:* TEdit97: Fixed problem with border not redrawing properly when Enabled was toggled at design time.

**1.77** (2/26/01)

-   Added new OrderedControls property to TToolbar97.
-   Made TToolbarButton97.Canvas a public property.
-   Revised the [Toolbar97 License](License.txt).
-   *Fix:* There was a possible AV problem in TB97Ctls' internal TDropdownList class.

**1.76b** (1/5/01)

-   *Fix:* If a toolbar on an MDI child form was floating, and the MDI parent form was minimized, the application would freeze up. A workaround for this has been added. I'm inclined to call this an OS bug because the freeze only occured on Windows 9x (not NT/2000).
-   *Fix:* On TToolbarButton97, when DropdownCombo and Down were both True, opening the dropdown menu would make the button temporarily redraw itself with an "up" appearance.
-   *Fix:* If a TToolWindow97 changed from a floating to a docked state when it had no handle, child controls may not have realigned properly.
-   TToolbar97.OnClose, OnCloseQuery, and OnVisibleChanged weren't documented. Fixed.

**1.76a** (9/11/00)

-   *Fix:* When the ButtonsStayDown variable was set to False, clicking on a TToolbarButton97 that had a dropdown menu would cause the button to be redraw in an "up" state immediately. Buttons that have dropdown menus now always behave as if ButtonsStayDown were set to True.
-   *Fix:* Fixed TDock97.RemoveBlankRows. Previously, if you tried to set the DockRow property of a toolbar to a number more than one past the last actual row number on the dock, it would erroneously clip it to half that number. For example, if you set DockRow to 1000, it would clip DockRow to 500. Now it properly clips to 0.

**1.76** (6/23/00)

-   Fixed an issue with the *OrderIndex* property of TToolbar97. Previously, *all* child controls on a TToolbar97 were added to the *OrderIndex* array, including those that weren't immediate children of the toolbar. That was not how I intended it to function. It now only includes controls that are immediate children (those which have their *Parent* properties set to the toolbar).
-   On TToolbar97/TToolWindow97, the OnMouseUp event handler is now triggered with X,Y coordinates of (-1, -1) when the user releases the left mouse button after dragging a toolbar. Previously, the OnMouseUp handler was never called when that happened.
-   Published *Font* and *ParentFont* properties on TToolbar97 and TToolWindow97. These properties aren't directly used for anything in Toolbar97, but child controls will inherit the toolbar's font if their *ParentFont* properties are set to True.
-   Made the *GetHighestRow* function on TDock97 public (a user request).
-   Setting "Position := Position" on a dock that contained docked toolbars resulted in the "Cannot change Position of a TDock97 if it already contains controls" exception. It now checks if *Position* is actually being assigned a different value before raising the exception.
-   Fixed a little problem with the *TB97\_cb5* C++Builder 5 package: it was compiling into a package named "TB97\_cb4.bpl" instead of "TB97\_cb5.bpl".
-   It turns out that Delphi 5's command line compiler has the same bug as Delphi 4 -- no EXE is created if the code contains an {\$ObjExportAll On} compiler directive. TB97Ver.inc has been updated to not include that directive on Delphi 5.

**1.75e** (3/10/00)

-   Added new package source file *TB97\_cb5* for C++Builder 5.

**1.75d** (1/27/00)

-   Floating toolbars no longer draw their non-client area while loading; the calls are deferred until after the component has finished loading. There were no confirmed reports of anyone needing this change, but I decided to implement it anyway. It may give a slight speed increase.

**1.75c** (1/5/00)

-   Added *OnMouseDown*, *OnMouseDown*, and *OnMouseUp* events to TDock97. *(Modified TDock97 declaration and TDock97.Create.)*
-   *Fix:* In very specific cases, after being clicked a flat TToolbarButton97 button may have still displayed its raised border even when the mouse cursor was no longer inside the button. *(Modified TToolbarButton97.Click.)*
-   *Fix:* In rare cases where there was an unusually tall control on a floating toolbar, the toolbar couldn't be resized to be as thin as possible. *(Modified TCustomToolbar97.BuildPotentialSizesList.)*

**1.75b** (11/9/99)

-   *Fix:* Continuing on version 1.75a's fix, changing the *FullSize* property of a toolbar docked to a TDock97 that has *Parent* set to *nil* no longer raises an exception.

**1.75a** (10/26/99)

-   *Fix:* Toolbars can now be docked to TDock97's that have *Parent* set to *nil*, without an exception being raised.

**1.75** (10/20/99)

-   Toolbars can now be docked to TDock97's inside other TDock97's.
-   Added new *HighlightWhenDown* property to TToolbarButton97. By default this property is True. When False, the dithered pattern will not be shown when the button's *Down* property is True.
-   *Fix:* On the first line of TB97\_d5.dpk, it read "package TB97\_d4".

**1.74d** (9/11/99)

-   Added a package file, TB97\_d5.dpk, for Delphi 5. No changes had to be made to the Toolbar97 source code for it to be Delphi 5-compatible. Please see the Toolbar97 Documentation for complete installation instructions.

**1.74c** (9/8/99)

-   Added *DoMove* protected method to TCustomToolWindow97 for compatibility with Andrew Cher's TToolbar97withMenu2000.

**1.74b** (8/24/99)

-   *Fix:* A very minor glitch introduced in 1.71 has been corrected: in certain cases, if you clicked the right side of a docked toolbar and released the mouse button without moving the mouse, the toolbar would shift left a few pixels.

**1.74a** (8/23/99)

-   Added *{\$I TB97Ver.inc}* to top of *TB97Reg.pas* and *TB97Vers.pas* so they have the necessary compiler options.
-   On Delphi/C++Builder 3 and higher, the constants in *TB97Cnst.pas* are now *resourcestring*s.

**1.74** (8/19/99)

-   TToolbarButton97 no longer references TCustomToolWindow97, resulting in a 30KB size drop if TToolbar97 or TToolWindow97 isn't used in a project.
-   The *IniLoadToolbarPositions* and *IniSaveToolbarPositions* functions now have *SectionNamePrefix* parameters, which allow you to customize the name of the sections the toolbar data is written to. See the documentation for more information.
-   *Fix:* Two problems dealing with toolbars on *FormStyle=fsStayOnTop* forms fixed. First, if a toolbar was initially floating on a *FormStyle=fsStayOnTop* form, it would appear behind the form when the program was started. Also, toolbars on *FormStyle=fsStayOnTop* forms in certain cases would cause the form to lose its topmost style.
-   Code size optimizations made to *TToolbarButton97.Paint* which trimmed off 268 bytes.

**1.73** (8/2/99)

-   Added *Version* property to all the components.
-   Added *OnCloseQuery* event to TToolbar97/TToolWindow97. This event is declared and operates the same way as a form's OnCloseQuery event.
-   Added *DropdownArrowWidth* property to TToolbarButton97, which lets you customize the width of the arrow portion of a button which has *DropdownCombo* set to True.
-   Added *OnMouseDown*, *OnMouseMove*, and *OnMouseUp* events to TToolbar97 and TToolWindow97.
-   Added *ControlIs97Control*, *Register97ControlClass*, *Unregister97ControlClass* procedures to *TB97Ctls.pas*. These should only be useful to component developers. Normally when a *TEdit97* control has the focus, moving the mouse over other *TEdit97* controls will not change the appearance of their border. If you need to know if a *TEdit97* or other "97" control registered with *Register97ControlClass* has the focus, you can call *ControlIs97Control(Screen.ActiveControl)*.
-   Added WM\_PRINT and PRINTCLIENT handlers to TDock97, TCustomToolWindow97, and TEdit97 for full compatibility with the component [Transition Effects](http://www.teechart.com/formcontainer/).

**1.72** (7/26/99)

-   Added *BeginMoving* and *BeginSizing* public methods to TToolbar97/TToolWindow97. See the documentation for information.
-   Two modifications made for compatibility with an upcoming version of AnimatedMenus/2000: added *BuildPotentialSizesList* protected method to TToolbar97, and added new overridable *DoDockChangingHidden* method to TToolbar97.
-   Floating tool windows now assign a unique *Name* to the internally created *TFloatingWindowParent* components. In previous versions, reading in components at run-time that had no name caused them to get assigned names like "\_1" because a component with no name -- the TFloatingWindowParent form -- already existed.

**1.71** (6/9/99)

-   Added new *CloseButtonWhenDocked* property to TToolbar97/TToolWindow97. When True, a Close button is displayed when the toolbar is docked.
-   *Fix:* When *FixAlign* was True on a TDock97, the one-pixel strip displayed when no toolbars are docked was not being painted properly in certain cases. *(Modified TDock97.WMNCPaint.)*
-   *Fix:* When a dropdown menu was assigned to a TToolbarButton97, if *GroupIndex* was nonzero the *Down* property would be toggled whenever the dropdown menu was displayed. Now it only toggles the *Down* property if *DropdownCombo* is True and the left side of the button is clicked. *(Modified TToolbarButton97.Click.)*

**1.7c** (5/29/99)

-   The RegLoadToolbarPositionsEx and RegSaveToolbarPositionsEx were not callable on C++Builder. This was because in C++ code the *HKEY* type is declared as a pointer, but in Pascal *HKEY* is an integer. So this caused a conflict. The RootKey parameter has been changed from type *HKEY* to *DWORD* to work around this problem. In C++Builder you will still have to use a *DWORD* typecast to call it, for example:
    RegSaveToolbarPositionsEx(this, (DWORD)HKEY\_LOCAL\_MACHINE, "Software\\Test");
-   *Fix:* RegLoadToolbarPositionsEx and RegSaveToolbarPositionsEx were creating empty keys under HKEY\_CURRENT\_USER if the *RootKey* parameter wasn't HKEY\_CURRENT\_USER.
-   Optimized TCustomToolWindow97.DrawDraggingOutline.CreateHalftoneBrush. 40 bytes less code now! :-)

**1.7b** (5/21/99)

-   *Fix:* The *OnInsertRemoveBar* event of TDock97 did not work properly in 1.7a. Fixed.

**1.7a** (5/20/99)

-   Many major improvements have been made regarding the dock code:
    -   TToolbar97/TToolWindow97 now have a *LastDock* property. When a toolbar is docked this property is synchronized with DockedTo, but when a toolbar changes to a floating state it points to the dock it was docked to last. Double-clicking a floating toolbar will restore it to the dock specified by *LastDock*, and at the same position it previously was docked at. This property overrides and is meant to be a replacement for *DefaultDock*. If you want, you can have it not use the new *LastDock* property by setting the *UseLastDock* property to False.
    -   If a docked toolbar is hidden and then shown again, its position remains the same.
    -   When the form is resized to where some docked toolbars had to be shifted left to remain fully visible, increasing the width of the form back now restores the toolbars' original positions (like Office 97).
-   Added *ShowCaption* property TToolbar97/TToolWindow97.
-   Docked toolbars with the *FullSize* property set to True no longer flicker while the form is being resized.
-   ShowHint is now set to True on the internal class TFloatingWindowParent. This way you no longer have to explicitly set ShowHint to True on your toolbars or the controls on them to get their hints to appear when the toolbar is floating.
-   Added a special handler for WM\_QUIT to TB97Ctls.pas's PeekMessage call, as was done with ValidateDockedNCArea in TB97.pas in Toolbar97 1.69c.
-   Various code optimizations and tweaks.

**1.69d** (5/4/99)

-   *Fix:* RegLoadToolbarPositionsEx and RegSaveToolbarPositionsEx did not work if their RootKey parameters weren't HKEY\_CURRENT\_USER. I wasn't aware that on TRegIniFile if RootKey is changed, OpenKey must be called to reopen the registry key. *(Changed RegLoadToolbarPositionsEx & RegSaveToolbarPositionsEx.)*

**1.69c** (5/4/99)

-   *Fix:* A call to PeekMessage during the painting of the non-client area of TToolbar97/TToolWindow97 was removing WM\_QUIT messages from the message queue, meaning a request to close if the application would be ignored if the non-client area was painting at that time. It now reposts WM\_QUIT messages if it encounters one. *(Changed TCustomToolWindow97.ValidateDockedNCArea.)*

**1.69b** (5/2/99)

-   *Fix:* In certain cases, the SetSlaveControl method of TToolbar97 did not work -- it was getting the top/bottom and left/right versions backwards. *(Changed TToolbar97.SetControlVisible and optimized TToolbar97.OrderControls.)*

**1.69a** (4/6/99)

-   *Fix:* Fixed a nasty problem introduced in yesterday's version 1.69, related to the addition of the new FloatingMode property. It seems there is an undocumented difference (or should I say bug?) in the way the Win32 function SetWindowPos behaves on Windows 95/98 as opposed to NT. This was causing, in certain cases, the application to not activate properly or even appear to hang when multiple toolbars were floating. I do most of my development and testing on Windows NT and wasn't aware of this until now. Sorry for the inconvenience. *(Changed TCustomToolWindow97.UpdateTopmostFlag.)*

**1.69** (4/5/99)

-   Added DockMode property to TToolbar97/TToolWindow97. Using this property you can now prevent toolbars from being undocked while still permitting them to be moved.
-   Added FloatingMode property to TToolbar97/TToolWindow97. You can have a floating toolbar stay on top of all forms by setting this property to *fmOnTopOfAllForms*.
-   *Fix:* On NT, if another process took the focus while you were in the middle of dragging a toolbar, remnants of the dragging rectangle might have been left behind on the screen. Obviously that's rarely encountered and not a biggie, but it was still worthy of a fix. :-) *(Changed TCustomToolWindow97.BeginMoving & BeginSizing.)*

**1.68a** (3/4/99)

-   Added new package source file *TB97\_cb4* for C++Builder 4.

**1.68** (2/20/99)

-   Added DropdownAlways property and OnDropdown event to TToolbarButton97. *(Changed TToolbarButton97 declaration, TToolbarButton97.Click, and TToolbarButton97.SetDropdownMenu. Added TToolbarButton97.SetDropdownAlways.)*
-   Added OnDockChangingEx and OnDockChangingHidden events to TToolbar97/TToolWindow97. *(Changed TToolbar97, TToolWindow97 declarations, and TCustomToolWindow97.SetParent.)*
-   TToolbar97.SetSlaveControl can now be called with *nil* in one of the parameters. This can be useful if you want a top/bottom docked version of a control, but no left/right version. *(Changed TCustomToolbar97.SetControlVisible.)*
-   *Fix:* Added workaround for Delphi 2 & C++Builder 1 TBitmap bug that, in certain cases, caused backgrounds on docks to not be displayed properly. *(Changed TDock97.DrawBackground.)*

**1.67b**

-   Multiple display monitors under Windows 98 are now properly supported. In previous versions, it wasn't letting floating toolbars be dragged outside the primary display monitor. I haven't tested the multiple monitor support on NT 5 since I don't have it, but it should work since NT 5 shares the same set of multiple monitor APIs as Windows 98.
-   TB97Ver.inc modified to work around an apparent bug in the Delphi 4 command line compiler. The {\$ObjExportAll On} directive which was put in for C++Builder 3 caused the Delphi 4 command line compiler to not generate an output .EXE for some reason. Now it has an {\$IFNDEF VER120} directive around it so that it isn't included when compiling on Delphi 4.

**1.67a**

-   On Delphi 4, the HelpContext property of TToolbarButton97 is now properly synchronized with the action's HelpContext property.
-   Removed the TToolWindowArrangeType declaration in tb97.pas. It was causing a conflict with TurboPower's Async Pro since it declares an *atNone* too, and wasn't being used by anything anyway.

**1.67**

-   Improved ActiveX compatibility. Thanks to Alan Bellingham for providing me with the fixes. *(Changed GetToolWindowParentForm and added TFloatingWindowParent.CreateParams.)*
-   Publicized the DockedTo, DockPos, and DockRow properties of TCustomToolWindow97. This way when you reference a toolbar using the Toolbars property of a dock, you don't have to use a typecast to use these properties.
-   Added new RegLoadToolbarPositionsEx and RegSaveToolbarPositionsEx functions. These add a new root key parameter (RootKey) than the non-Ex versions don't have. There is no reason I can think of why you'd want to save toolbar settings to a key other than HKEY\_CURRENT\_USER (as this would classify as a "per-user" setting), but this capability was requested.
-   Added new public property FloatingWidth to TToolbar97 which allows you to get or set the current width of a floating toolbar in your own code.
-   Published Anchors and Constraints properties in TToolbarButton97 on Delphi 4.
-   Published Anchors, BiDiMode, Constraints, DragKind, ParentBiDiMode, and OnEndDock properties in TEdit97 on Delphi 4.

**1.66e**

-   *Fix:* When compiling on Delphi 4 with range checking enabled, a range check error may have occured in the CBTHook procedure of TB97Cmn.pas. Fixed by adding an HWND typecast. (Don't we just hate Delphi 4 and its unsigned integers?)

**1.66d**

-   *Fix:* On TDock97's with a border, two OnResize events (instead of one) were getting fired whenever a tool window was docked for the first time. *(Changed TDock97.WMNCCalcSize, TDock97.WMNCPaint, and TCustomToolWindow97.BeginMoving.MouseMove.CheckIfCanDockTo.)*

**1.66c**

-   *Fix:* Problem with using Toolbar97 as a run-time package in C++Builder 3 finally solved. It turns out there's a special compiler directive that must be used when compiling Pascal code into a C++Builder 3 package. *(Modified TB97Ver.inc.)*

**1.66b**

-   *Fix:* OnResize events on TDock97 and TCustomToolWindow97 descendants are now only called once the component is finished loading. In certain cases earlier versions had been calling these events *before* the parent form's OnCreate event handler was called. *(Changed TDock97.WMSize and TCustomToolWindow97.WMSize.)*

**1.66a**

-   *Fix:* On certain situations, a runtime error 216 may have been raised if you called Halt while the Toolbar97 controls were being used. *(Changed TB97Cmn.pas finalization section.)*

**1.66**

-   Replaced DragHandle property on TCustomToolWindow97 and descendants with a new property called DragHandleStyle, which adds the ability to create IE4-style single drag handle toolbars.
-   Added Default and Cancel properties to TToolbarButton97.
-   Added BorderStyle property to TCustomToolWindow97 and descendants. Useless for most purposes, but several had requested a property like this.
-   *Fix:* When 256-color glyphs were used on a TToolbarButton97 control the bitmaps were being converted to device-dependent bitmaps when the form was saved, resulting in loss of the bitmap's palette if the display was set to a non-palettized mode (e.g. 16- or 24-bit color). This bug affected *only* Delphi 2 and C++Builder 1.

**1.65f**

-   *Fix:* After the change to fix Action synchronization in 1.65d, a new problem surfaced. On Windows 95/98, a "Stack Overflow" error occured in certain cases if the form was closed while a floating tool window was focused.

**1.65e**

-   *Fix:* If Repeating was set to True on a TToolbarButton97 control and Flat and Opaque were not True, the control was not being repainted correctly.
-   On Repeating=True buttons, TToolbarButton97 now calls the Click method instead of "inherited Click". This change only affects TToolbarButton97 descendants.

**1.65d**

-   Added Color property to TToolbarButton97.
-   *Fix:* Controls that used Actions on floating toolbars were not being properly synchronized in certain cases. *(Changed TFloatingWindowParent.CMShowingChanged.)*
-   *Fix:* Having a TPageControl on a floating TToolWindow97 caused an exception when the form was closed. The "bug" is actually in TPageControl -- I wasn't aware of it when testing version 1.65. *(Removed TCustomToolWindow97.CreateWnd.)*
-   *Fix:* If a TToolbarButton97 was disabled and its Down property was then set to True, it would be redrawn as if it were enabled. *(Changed TToolbarButton97.SetDown.)*
-   *Fix:* When Escape was pressed while a floating toolbar was focused, it would make a beep sound after focusing the form. *(Changed TFloatingWindowParent.CMDialogKey.)*

**1.65c**

-   Fixed a bug in TToolbarButton97 that might having been causing an access violation on program exit. Only one person has reported this, so I don't think it was a widespread problem. *(Modified TToolbarButton97.Destroy & TToolbarButton97.Notification.)*
-   Moved compiler options from TB97.pas to TB97Ver.inc so they can be included in all units, and added {\$I TB97Ver.inc} to the units that didn't already have it.

**1.65b**

-   Fixed (rarely encountered) problem repainting problem on floating toolbars introduced in 1.65. *(Removed TCustomToolbar97.CreateParams/WMSize methods.)*
-   Fixed problem introduced in 1.65 with floating toolbars not being loaded with the correct size.

**1.65a**

-   Fixed two bugs that were introduced in version 1.65's TToolbarButton97 component. Buttons with DropdownCombo=True were calling their OnClick handler when the dropdown menu is displayed, and text wasn't showing on buttons with DisplayMode=bmTextOnly. (Sorry about that!)
-   A reported problem regarding a "list index out of bounds" error in TDock97.ArrangeToolbars should also be fixed. (I haven't gotten confirmation on this yet though.)
-   Two minor changes: TToolbarParams record has been moved from TB97.pas to TB97Tlbr.pas where it should be, and the MoveOnScreen(True) call has been removed from TCustomToolWindow97.SetParent's UpdateFloatingToolWindows procedure.

**1.65**

-   To make things easier to manage, the source code to the Toolbar97 components has been split into seven smaller .pas files instead of one big file. Please read the *Installation* section of the documentation for revised installation instructions.
-   Added Action property to TToolbarButton97 (Delphi 4 only).
-   Image lists can now be used with TToolbarButton97 through the new Images and ImageIndex properties.
-   Added AddDockForm and RemoveDockForm methods to TCustomToolWindow97 and descendants.
-   Added BeginUpdate and EndUpdate methods to TDock97.
-   Added Visible property to TToolbarSep97.
-   Added global variable ButtonsStayDown.
-   Floating tool windows are now drawn with gradient captions under Windows 98 & NT 5.
-   TCustomToolWindow97's can now be placed on non-TForm forms, like ActiveForms.
-   ClientWidth and ClientHeight properties of TToolWindow97 renamed to ClientAreaWidth and ClientAreaHeight. Internal changes to the code necessitated this.
-   TCustomToolWindow97 and descendants are now initially created with a Parent of nil, like other VCL controls. This means that dynamically created toolbars will not appear on the screen until you assign to either Parent or DockedTo. Previous versions automatically set DockedTo to nil and assigned a parent.
-   Assigning to TCustomToolWindow97.Parent and TCustomToolWindow97.DockedTo is now interchangable.
-   Floating TCustomToolWindow97's no longer appear in the parent form's tab order.
-   At design time, when the Visible property of a control on a TToolbar97 is set to False, it no longer loses its position in the toolbar's control arrangement.
-   When Esc is pressed while a control on a TCustomToolWindow97 is focused, activation now returns to the form.
-   Public FloatingPosition property added to TCustomToolWindow97.
-   On TCustomToolWindow97, CreateWnd now fails if Parent=nil.
-   *Fix:* TCustomToolWindow97's internal FloatParents are now freed upon Destroy. In previous versions, they were not freed which may have resulted in a memory leak if your application created and freed toolbars dynamically.
-   *Fix:* A WS\_THICKFRAME style is no longer set on TCustomToolWindow97's whose Resizable property is set to False. Previous versions were allowing the user to resize tool windows even when Resizable=False by using the size grip.
-   *Fix:* There was a serious but rarely encountered bug in TToolbarButton97's glyph routines. If a glyph had more than 16 colors and a width that was not a multiple of 8, the resulting button would look corrupted and/or a crash of the program would occur. *(Changed the internal procedure GenerateMaskBitmapFromDIB.)*
-   Many other minor tweaks and fixes.

**1.63**

-   TToolbarButton97 now consumes amount the same amount of GDI resources as Toolbar97 versions prior to 1.6 did. In versions 1.6-1.62 I had the TBitmap.Dormant calls taken out because of a little quirk in Delphi 3's TBitmap (bitmaps are converted to bmDIBs after a call to Dormant), but it turns out this was causing more problems than it was solving. In certain cases on Windows 95 this was causing "low on resources" messages in applications with a *lot* of buttons. If you desire, you can still disable the Dormant call in 1.63 at run-time by setting the TToolbarButton97's new CallDormant property to False before assigning a new Glyph.

**1.62**

-   Added DragHandle property to TToolbar97.
-   Added Repeating, RepeatDelay, and RepeatInterval properties to TToolbarButton97.
-   Added OnRequestDock event to TDock97.
-   Renamed all references of "TToolbar97" to "TCustomToolbar97".
-   TToolbar97 is now a descendant of TCustomToolbar97.
-   Fixed a little problem with 1.61's new FullSize property: Resetting FullSize to False on a TToolbar97 now properly restores its size.

**1.61**

-   Added FullSize property and OnResize event to TToolbar97 and TToolWindow97.
-   Floating TToolbar97's and TToolWindow97's can no longer be dragged off the top of the screen. It now ensures that at least a portion of the title bar is always visible.
-   Redisabled child control alignment on TToolbar97's, like it was in 1.53 and earlier. (I inadvertently enabled it in 1.6, but it was never meant to work.)
-   Fixed a couple of places where invalid parameters were being passed to API calls.

**1.6**

-   Added a new component, TToolWindow97.
-   Added ActivateParent and HideWhenInactive properties to TToolbar97 and TToolWindow97, replaced the CanDockLeftRight property with the more flexible DockableTo, and published the TabOrder property. Added GlyphMask, ModalResult, NoBorder, and ShowBorderWhenInactive properties to TToolbarButton97.
-   Added BackgroundOnToolbars property to TDock97.
-   TToolbarButton97 now properly supports 16- and 24-bit glyphs on Delphi 3 only. (It now includes workaround code in order to be compatible with all video drivers.) But it is recommended that you stick to 16 color bitmaps on Delphi 2 and C++Builder, because of limitations of their VCLs.
-   The DropdownMenu support in TToolbarButton97 improved to allow selection of menu items without having to click and release the button.
-   Changing a form's properties such as BorderIcons or Position at run-time no longer cause the toolbars to behave strangely. (In more technical terms, this was because changing those properties caused the form to call RecreateWnd, causing the toolbar's hook to be removed. It now uses a different method of trapping form messages.)
-   Fixed the momentary flickering problem that was visible while dynamically creating an MDI child form that contained an initially floating toolbar. This fix also corrects a reported problem dealing with toolbars on modal forms.
-   Many other minor fixes, modifications, and optimizations.

**1.53**

-   A last minute release to fix the access violation problem introduced in 1.52 when you tried deleting a TToolbar97.

**1.52**

-   TToolbarButton97 now supports buttons split into two parts (like the Undo and Redo buttons in Office 97) through the new DropdownCombo property.
-   Now includes a good selection of "standard" glyphs that I've collected. See the Glyphs.zip file.
-   Disabled glyphs are now generated differently. They now look just like Office 97 (and MFC). But for backward compatibility, you can still use the "old" TSpeedButton disabled look by setting the new OldDisabledStyle property to True.
-   Finally has support for a new fifth "mouse in" glyph, if you want to add an IE or Communicator look to your buttons. See the updated description of the Glyph property of TToolbarButton97.
-   Added ToolbarCount and Toolbars properties to TDock97.
-   Added a Flat property to TToolbarButton97.
-   Added SizeHorz and SizeVert property to TToolbarSep97.
-   Numerous small improvements and minor fixes. See the source code for details.

**1.51**

-   Added new OnMouseEnter and OnMouseExit events to TToolbarButton97.
-   In certain custom color schemes, buttons glyphs were invisible (very rare though). This wasn't a bug in Toolbar97, but is a bug in the VCL class TCustomImageList. It now works around it.
-   No longer calls the OnRecreating/OnRecreated events while a toolbar is being destroyed.
-   Now should be fully compatible with Warren Young's TMSOfficeCaption component, but *only*with version 1.41 or later of it. If you have an earlier version, go to [http://www.ee.ed.ac.uk/\~wfy/components.html](http://www.ee.ed.ac.uk/~wfy/components.html) and get the latest.
-   A few more minor improvements.

**1.5**

-   OrderIndex property added to TToolbar97 to make arranging controls at run-time much easier.
-   Delphi 1 support had to be removed, since it wasn't compatible with the new arranging method. Sorry, but it's time to move on.
-   Added an AllowDrag property to TDock97.
-   Added a Blank property to TToolbarSep97.
-   Added an OnResize event to TDock97.
-   Docks can now be placed inside controls other than a form. I can't think of a reason why you'd want to do this, but some people have requested this.
-   All known problems fixed, and a couple of small improvements.

**1.47**

-   Rewrote most of moving and resizing routines to make it work exactly like Office 97.
-   Added a DisplayMode property to TToolbarButton97.
-   Toolbars now work flawlessly on MDI child forms.
-   A few other minor improvements and fixes.

**1.46**

-   Added a LimitToOneRow property to TDock97.
-   C++Builder transparency problems in 1.45 fixed.
-   A minor disabled glyph transparency problem that affected Delphi 2 and C++Builder fixed.
-   Some minor improvements.

**1.45**

-   Dropdown menus now fully supported on TToolbarButton97.
-   Backgrounds on TDock97's now supported. See Background property.
-   Added a FixAlign property to TDock97.
-   Added a WordWrap property to TToolbarButton97.
-   The problems in 1.4 fixed.
-   A lot of little problems that have been around since 1.3 fixed (see source code for details).

**1.4**

-   Now supports Delphi 1 also.
-   Loading and saving toolbars' positions is now done with procedures called RegLoadToolbarPositions and RegSaveToolbarPositions for loading and saving to the registry, and IniLoadToolbarPositions and IniSaveToolbarPositions for loading and saving to .INI files. This corrects a problem that sometimes caused toolbars to be loaded incorrectly.
-   Fixed minor flickering problem while dragging.
-   Now prevents you from dropping a toolbar under the taskbar (32-bit only).
-   Several minor, but annoying, problems fixed. See source code for details.
-   A lot of tweaks to the source code.

**1.37**

-   Fixed problem of floating toolbars sometimes reappearing (without the program telling them to) after you closed them.

**1.36**

-   Fixed a couple of very minor and insignificant cosmetic problems. See the source code for details.

**1.35**

-   Fixes all known problems, including the rather serious problem in TToolbarButton97 of it sometimes displaying the wrong glyphs in Delphi 2.
-   Several more problems fixed. See the source code for details.

**1.33**

-   Added a TEdit97 component.
-   Fixed a lot of minor but noteworthy problems. See the source code for details.

**1.32**

-   Fixed another minor problem in TToolbar97 that caused it to sometimes incorrectly reorder the controls.

**1.31**

-   Fixed problems with loading the demo application.
-   Fixed a very minor problem in TToolbarButton97.

**1.3**

-   Floating toolbars are now resizable. Like Office 97, they also now hide themselves when the application is deactivated.
-   Separators are no longer automatically created. You now create them using the TToolbarSep97 component.
-   Added a CanDockLeftRight property to TToolbar97.
-   Added an Opaque property to TToolbarButton97. Also made the buttons now stay down until it returns from the OnClick handler, like Office 97.
-   A *lot* of small fixes on all of the controls (too many to mention) to make them work more like Office 97.
-   C++Builder now supported.

**1.2**

-   Left and right side docking now supported. A SetSlaveControl method added to TToolbar97 for designating top/bottom docked and left/right docked versions of controls on the toolbar.
-   A lot of little problems fixed.

**1.11**

-   Added a CloseButton property to TToolbar97.
-   More bug fixes.

**1.1**

-   Delphi 3 now supported!
-   TToolbarButton97 component completely redesigned. Now it works exactly like a TSpeedButton. I also borrowed some of the glyph caching techniques used in Delphi 3 to make it much faster.
-   Added a Color property to the TDock97 and TToolbar97 controls so it now looks right in MDI forms.
-   TToolbar97's BarHeight property is no longer global to the whole application, as this sometimes caused problems. Now each toolbar has an individual BarHeight setting, which allows for greater flexibility.
-   Many design mode problems fixed. (And you can now move docked toolbars!)

**1.0**

-   First release.

