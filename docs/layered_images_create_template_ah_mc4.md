[Create an Image Template](layered_images_create_template_co4)
 > Citrix MCS for Nutanix AHV
#Create Image Templates (MCS for Nutanix AHV)
In this article:
<table>            <col></col>            <tbody>                <tr>                    <td>                        <p><a href="#Pre"> Prerequisites</a>                        </p>                        <p><a href="#Cr_Temp"> Create an Image Template</a>                        </p>                        <p><a href="#Next"> Next Step</a>                        </p>                    </td>                </tr>            </tbody>        </table>
You can create Image Templates to publish Layered Images to your target platform where you can then use the Layered Image to provision servers on your chosen publishing platform. An Image Template stores your Layer assignments, along with a Layer icon and description. You can easily [edit](layered_images_manage_template_co4.htm#Ed_Temp)[ an Image Template and use it to publish new versions of your Layered Images. ](layered_images_manage_template_co4.htm#Ed_Temp)
##Prerequisites<a name="Pre"></a>
<ul>            <li>                <p><a href="layer_os_create_ah4.htm">OSLayer</a> (Required) </p>            </li>            <li>                <p><a href="layer_os_create_ah4.htm"></a><a href="layer_platform_create_ah4.htm">Platform Layer</a> (Required for cross-platform deployments)</p>                <p>The Platform Layer contains the software required for publishing to your environment, in this case:</p>                <ul>                    <li>Nutanix Acropolis VM Mobility</li>                    <li>Citrix MCS Device imaging tools</li>                </ul>                <p>The Platform Layer must have the same hardware settings as the OSLayer. You choose these settings when deploying the VM for the OSand Platform Layers.</p>            </li>            <li>                <p><a href="layer_apps_create_ah4.htm">App Layers</a> (Optional)</p>                <p>You can create an Image Template without App Layers. This is useful for testing your OSLayer before using it to create App Layers. </p>            </li>        </ul>
##Create an Image Template<a name="Cr_Temp"></a>
To create an Image Template:
<ol>            <li>In the Unidesk Management Console (UMC), select the <b>Images</b> module, then click <b>Create Template</b>. This opens the Create Template wizard.</li>            <li>In the Name and Description tab, enter a <b>Name</b> for the template and notes in the <b>Description</b> field, so you can identify the template when choosing one for publishing a Layered Image. </li>            <li>In the OSLayer tab, select one of the <b>Available OSLayers</b>. If there is more than one Layer Version, the most recent version is selected by default. You can choose an older version by expanding the Layer and choosing a different one.</li>            <li>In the App Assignment tab, select the <b>App Layers</b> to include in the Layered Images that you publish using this template.</li>            <li>                <p>On the Connector page, select a CitrixMCS for Nutanix AHV Connector Configuration for the location where you want to publish the Layered Image. </p>                <p>If you do not yet have a Connector Configuration for CitrixMCS for Nutanix AHV, add one. Click <b>New</b>, choose the Connector Type, and follow the instructions to <a href="connector_config_fields_ah_mc4.htm">Create a Connector Configuration</a>.</p>            </li>            <li>                <p>In the Platform Layer tab, select aPlatform Layer with the tools and hardware settings that you need to publish Layered Images to your environment. For details, click <a href="#platform_layer_prereqs">here</a>.</p>            </li>            <li>                <p>On the Layered Image Disk page, edit the following fields, as needed:</p>                <ul>                    <li>(Optional) <i>Layered Image Disk File name</i>. Enter a name for the Layered Image Disk.</li>                    <li><i>Layered Image Disk Size</i>. The default disk size of 100 GB is recommended.</li>                    <li><i>Layered Image Disk Format</i>. The default disk format is VHD, but you can also select VMDK or QCOW2.</li>                    <li><i>Elastic Layering</i> - Controls whether Elastic Layering  on this Layered Image is allowed. To allow Elastic Layers for users of this Layered Image, select <b>Application Layers only</b>. Otherwise, select <b>None</b>.</li>                </ul>            </li>            <li>On the Confirm and Complete tab, enter any comments you would like for this layer, and click <b>Create Template</b>.</li>        </ol>
The new Template icon appears in the Unidesk Images module.
##Next Step<a name="Next"></a>
[ Publish Layered Images (MCS for Nutanix AHV)](layered_images_publish_ah_mc4)[        ](layered_images_publish_ah_mc4)