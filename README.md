# xamarin-forms-book-preview-2
Sample code for the 2nd Preview Edition of *Creating Mobile Apps with Xamarin.Forms*.

Chapters of the book can be downloaded from http://developer.xamarin.com/guides/cross-platform/xamarin-forms/creating-mobile-apps-xamarin-forms/.

## Notes

### Now with Windows Runtime Projects!

Two additional projects have been added to every solution with the suffixes **WinApp** and **WinPhone81**. These projects target the Windows Runtime API in Windows 8.1 and Windows Phone 8.1, respectively.

The following problems will be experienced in the sample programs with the **WinApp** and **WinPhone81** projects:

- Font sizes are somewhat erratic
- `Device.OnPlatform` and `OnPlatform` don't account for the two new platforms (but see below)
- The SAP programs in Chapter 9 won't compile
- Some of the programs in Chapter 13 don't work (but see below)

To add the Windows Runtime projects to your own Xamarin.Forms solutions, see http://developer.xamarin.com/guides/cross-platform/xamarin-forms/windows/.

### Loading the NuGet Packages

The Xamarin.Forms NuGet packages are not part of these projects. They must be downloaded for each project.

To avoid hassles, start by loading the NuGet packages for the two solutions in the **Libraries** directory, and building those two projects. 

First load the **Libraries/Xamarin.FormsBook.Toolkit** solution into Visual Studio. Right-click the solution name in the **Solution List** and select **Manage NuGet Packages for Solution**. A notice should appear at the top of the **Manage NuGet Packages** dialog that says "Some NuGet packages are missing from this solution. Click to restore from you online package sources." Click the **Restore** button and then the **Close** button. Build the library.

Do the same thing with the **Libraries/ElPasoHighSchool** solution.

You can then load any of the application projects. For each project, again right-click the solution name, select **Manage NuGet Packages for Solution** and go through the same process.

### Differences with Book

For some programs, there are some differences between the code listings in the PDF book chapters and those in this repository: In Chapter 7, **TextVariations** is different because beginning with version 1.3.3, there is no longer a distinction between text as the content of the `Label` tags and text as content of the `Label.Text` tags. In both cases, whitespace at the beginning and end of the text block is trimmed.  

When specifying a `local` namespace declaration in XAML, it is no longer necessary to include the assembly name. You can include it if you want, but it's been removed from the **ColorListView** program in Chapter 8, **SharedStatics** in Chapter 10, and **StackedBitmap** in Chapter 13.

The deprecated `Font` has been replaced with `FontSize` in **MonkeyTap** and **XamlKeypad**, both in Chapter 8.

### Chapter 13 and Platform-Specific Bitmaps (July 22, 2015)

The four programs in the section of Chapter 13 entitled "Platform-Specific Bitmaps" have all been enhanced to run on the two Windows Runtime platforms.

To accomplish this, a `ForPlatform` class has been added to the **Xamarin.FormsBook.Toolkit** library. This class is very similar to `OnPlatform` except that it has two additional properties named `WindowsStore` and `WindowsPhoneStore`. These properties allow a code or XAML file to access bitmaps from the two Windows Runtime projects.

### F# Versions (August 30, 2015)

All the non-SAP solutions in Chapter 2 through 6 now exist in F# versions. These can be found in the FS directory of each of those chapter directories. 

The two solutions in Chapter 2 were created manually and include F# versions of the iOS and Android startup projects (but C# versions of all the Windows Phone and Windows startup projects). 
The solutions in Chapter 3 through 6 were created from the normal Xamarin.Forms solution template for C#, and then an F# project was substituted for the PCL.

These should be considered "experimental" at this point. None of the F# projects run on Windows Phone 8, and others that use reflection have issues with the two Windows Runtime platforms.

### Upgrade to version 1.5.1.6471 (November 6, 2015)

All solutions have been upgraded to Xamarin.Forms 1.5.1.6471. 

Two programs towards the end of Chapter 19 (**ConditionalCells** and **ConditionalSection**) previously did not work on Windows Phone, and the screenshot in the chapter showed a gray screen for that platform. The programs now run on Windows Phone as of version 1.4.4.6392 and the chapter has been updated.

### The Universal Windows Platform (UWP) (November 13, 2015)

All solutions now have a project with the extension **UWP**. This is a project that targets the Universal Windows Platform, which is implemented by Windows 10 and Windows Mobile 10.

With Xamarin.Forms 1.5.1.6471, these projects actually target the the Windows Runtime API (also known as the Windows Store API), which is a subset of the UWP, so these projects are basically the same as the **WinApp** projects.

To specifically target the UWP at the current time, you will need to download a ZIP file for a NuGet package with the version number 1.5.1.6466-pre2, and install that. This process is discussed in the Forums post [Xamarin.Forms for UWP Preview Now Available](https://forums.xamarin.com/discussion/54401/xamarin-forms-for-uwp-preview-now-available).