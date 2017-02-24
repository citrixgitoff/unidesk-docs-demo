You are here: Learn about Citrix App Layering [UnideskVersion Layering 4.0.8] > Layer > Layer essentials
#Layer Essentials
In this article:
<table>            <col></col>            <tbody>                <tr>                    <td>                        <p><a href="#OS&#160;Layer"> Layer Essentials</a>                        </p>                        <p><a href="#Platform"> Platform Layers</a>                        </p>                        <p><a href="#App"> App Layers</a>                        </p>                        <p><a href="#User"> User Layers (Unidesk Labs)</a>                        </p>                        <p><a href="#Verifyin"> Verifying Layers</a>                        </p>                    </td>                </tr>            </tbody>        </table>
##OS<a name="OS&#160;Layer"></a>##Layers<a name="OS&#160;Layer"></a>
###What is an OS<a name="What"></a>###Layer?<a name="What"></a>
An OS Layer includes the software and settings for the operating system that you deploy as part of your other layers and ultimately, your Layered Images. Once you have prepared the OS disk for deployment, you can create a Unidesk  Operating System Layer by importing the OS disk into a new Layer.
###Why layer my OS<a name="How2"></a>###image? <a name="How2"></a>
With an OSLayer, you can install your operating system once, and update it by adding a new Version to the Layer whenever there's a new patch or update. You can deploy this layer, or a version of it, in every image you publish. This allows you to maintain one OS image and use it to provision all of your servers.
###Can I deploy more than one OS<a name="How2"></a>###Layer? <a name="How2"></a>
If you need to support more than one operating system, for example, if you need both Windows Server 2012 R2 and Windows Server 2008 R2, you can create more than one OSLayer. However, each App Layer is only compatible with the OSLayer you use to create it, and if you deploy two OSLayers, you will also need to deploy a compatible App Layer for each one. Further, in future releases when deploying Elastic Layers to users, those layers will only be compatible with users' desktops that use the same OS Layer. 
If you can support your users with a single OSLayer, the work associated with creating and updating App Layers will be much reduced.
###Can I deploy more than one version of the same OS<a name="Can"></a>###Layer?<a name="Can"></a>
Each time you need to deploy operating system patches and updates, you will do so by adding a new Version to the OSLayer. You can continue to publish Layered Images using any version of the OSLayer.
###What do I need to create an OS Layer?<a name="What2"></a>
The prerequisites for creating an OSLayer include:
<ul>            <li>A <a href="welcome_platform_support_co4.htm#Session">Unidesk-supported operating system</a></li>            <li>Unidesk ELMand network file share installed and configured</li>        </ul>
###How do I start?<a name="How"></a>
See the steps to [Create an OS](layer_os_create_co4)[Layer](layer_os_create_co4)[.](layer_os_create_co4)
##Platform Layers<a name="Platform"></a>
A Platform Layer is a layer that includes platform-specific configuration settings, tools, and other software required for your OSand Apps to be installed in or to run in a particular environment. 
###Types of Platform Layers<a name="When"></a>
<ul>            <li>A Platform Layer for <i>Packaging</i> (required in some cases, see below)</li>            <li>Platform Layer for <i>Publishing</i> (always required)</li>        </ul>
####Platform Layer for packaging layers and versions
The only time you need a Platform Layer for Packaging layers is when your OSimage was created on a different hypervisor than the one where you are building your other layers. When  creating an App Layer or Layer Version, or OSVersions, the purpose of the Platform Layer is to ensure that any hypervisor-related software and settings are available during the installation of the application(s) on that layer, if needed. If you choose to use a Platform Layer for Packaging a layer, the hypervisor-related software will only be used during layer packaging, and has no effect on where you can publish the layer as part of a Layered Image. 
####Platform Layer for publishing Layered Images
A Platform Layer for Publishing is required when you publish Layered Images. The purpose of the Platform Layer for Publishing is to include the settings and software that the Layered Image needs to be deployed in your environment. When creating a Platform Layer for Publishing, Unidesk removes unselected (and unnecessary) tools and software related to the platforms you are not publishing to. This is to prevent any unnecessary platform software from slowing down the Layered Image when it runs in the target environment. 
###Get started with Platform Layers<a name="Get"></a>
For details about creating Platform Layers, see [ Create a Platform Layer ](layer_platform_create_co4)[.](layer_platform_create_co4)
##App Layers<a name="App"></a>
###What is an App Layer?<a name="What"></a>
An App Layer is a virtual disk containing one or more applications that you can use in Layered Images. You can combine an App Layer with any other App Layers and a Platform Layer, as long as the OS Layer used to create the App Layer is selected. 
With most applications, creating an App Layer is simple. In a few cases, it's best to start with tips from experienced users, so the Unidesk Forum includes [Application Layer Recipes](layer_apps_recipes_co4)[ that you can search for tips about a particular application before you start. ](layer_apps_recipes_co4)
###Get started with App Layers<a name="Get"></a>
To create an App Layer, you use the Create App Layer wizard to deploy a Packaging Machine in your environment and install the application on the Packaging Machine, leaving the application in the state you want it to be in for users. Then you finalize the Layer. 
To get started with App Layers, see [ Create an App Layer](layer_apps_create_co4)[.](layer_apps_create_co4)
##User Layers (Unidesk Labs)<a name="User"></a>
A User Layer is a virtual disk where a user's app data and configuration settings are saved. User Layers are created when you:
<ul>            <li>Publish a Layered Image with <i>Elastic Layering</i> set to <i>Application and User Layers</i>.</li>            <li>Users log into their desktops on the above Layered Image. </li>        </ul>
With User Layers enabled on the Layered Image, users can  install applications locally on their desktops, and the apps and their data will be saved in the User Layer.
Learn more about how to [ User Layers (Unidesk Labs)](#User)[.](#User)
##Verifying Layers<a name="Verifyin"></a>
###If there are Layer integrity messages during the finalization process<a name="Layer_Integrity_Check"></a>
Layer integrity messages let you know what queued tasks must be completed before a Layer is finalized. The new Layer or Version can only be finalized when the following conditions have been addressed:<a name="Layer_Integrity_Messages"></a>
<ul>            <ul>                <li>A reboot is pending to update drivers on the boot disk - please check and reboot the Packaging Machine.</li>                <li>A post-installation reboot is pending - please check and reboot the Packaging Machine.</li>                <li>An MSI install operation is in progress - please check the Packaging Machine.</li>                <li>                    <p>A Microsoft NGen operation is in progress in the background. </p>                    <p><b>Note:</b> If a Microsoft NGen operation is in progress, you may be able to expedite it, as described in the next section.</p>                </li>            </ul>        </ul>
###Expediting a Microsoft NGen operation <a name="Complete_MS_NGen_Operations"></a>
NGen is the Microsoft Native Image Generator.  It is part of the .NET system, and basically re-compiles .NET byte code into native images and constructs the registry entries to manage them.  Windows will decide when to run NGen, based on what is being installed and what Windows detects in the configuration.  When NGen is running, you must let it complete.  An interrupted NGen operation can leave you with non-functioning .NET assemblies or other problems in the .NET system.
You have the choice of waiting for the NGen to complete in the background, or you can force the NGen to the foreground. You can also check the status of the NGen operation, as described below. However, every time you check the queue status, you are creating foreground activity, which might cause the background processing to temporarily pause. 
Forcing the NGen to the foreground will allow you to view the progress and once the output has completed, you should be able to finalize the layer.
<ol>            <li>                <p>Force an NGen operation to the foreground. </p>                <p>Normally, NGen is a background operation and will pause if there is foreground activity.  Bringing the task into the foreground can help the task to complete as quickly as possible. To do this:</p>                <ol>                    <li>                        <p>Open a command prompt as Administrator.</p>                    </li>                    <li>                        <p>Go to the Microsoft .NET Framework directory for the version currently in use:</p><pre>cd C:\Windows\Microsoft.NET\FrameworkNN\vX.X.XXXXX</pre>                    </li>                    <li>                        <p>Enter the NGen command to execute the queued items:</p><pre>ngen update /force</pre>                        <p>This brings the NGen task to the foreground in the command prompt, and lists the assemblies being compiled. </p>                        <p><b>Note:</b> It’s okay if you see several compilation failed messages!</p>                    </li>                    <li>Look in the Task Manager to see if an instance of MSCORSVW.EXE is running. If it is, you must allow it to complete, or re-run <span>ngen update /force</span>.  Do <i>not</i> reboot to stop the task. You <i>must</i> allow it to complete.</li>                </ol>            </li>            <li>                <p>Check the status of an NGen operation</p>                <ol>                    <li>                        <p>Open a command prompt as Administrator.</p>                    </li>                    <li>                        <p>Check status by running this command:</p><pre>ngen queue status</pre>                    </li>                    <li>                        <p>When you receive the following status, the NGen is complete, and you can finalize the Layer.</p><pre>The .NET Runtime Optimization Service is stopped</pre>                    </li>                </ol>            </li>        </ol>