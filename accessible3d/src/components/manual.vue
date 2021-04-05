<template> 
    <v-container class="pa-0 ma-0" fluid> 
        <v-parallax
          :height="$vuetify.breakpoint.smAndDown ? 500 : 300"
          width="100%"
          src="../assets/background.jpg"
        >
          <v-container fill-height>
            <v-row class="mx-auto">
                <v-col class="text-center">
                    <span
                        :class="[$vuetify.breakpoint.smAndDown ? 'display-3': 'display-4']"
                        class="font-weight-black"
                        data-aos="zoom-in" data-aos-duration="3000"
                        >
                        LET'S GET STARTED
                    </span>
                </v-col>
            </v-row>
            <v-row class="pa-0 ma-0"> 
               <v-col align="right" justify="right" width=100%>  
                   <span data-aos="zoom-in" data-aos-duration="3000">
                    Click here to download the text version
                   </span>
               </v-col>
            </v-row> 
          </v-container>
        </v-parallax>
        <v-row class="px-10">
            <v-col>
                <v-timeline
                    :dense="$vuetify.breakpoint.smAndDown" 
                    data-aos="fade-in" data-aos-duration="3000" data-aos-delay="500"
                >
                    <v-timeline-item
                        :color="colors[0]"
                        icon="mdi-wrench"
                        fill-dot
                    >
                        <v-card
                            :color="colors[0]"
                            dark
                        >
                            <v-card-title class="title">
                            Software Installation
                            </v-card-title>
                            <v-card-text class="white black--text pt-2">
                                <p> 
                                    Before you can start generating models, you will first need to install the following software. In this guide we will be using both COLMAP (processess images and creates the model) and CloudCompare (visualizes the model) which are totally free and open-source! 
                                    We also reccomend you to install FFmpeg if you want to perform the reconstruction using a video instead of taking multiple photos. Click 'READ MORE' for detailed installation instructions!
                                </p>
                                <ul class="pb-5">
                                    <li> COLMAP (Download <a href="https://demuc.de/colmap/#download" target="_blank">Here</a>)</li>
                                    <li> CloudCompare (Download <a href="https://www.danielgm.net/cc/" target="_blank">Here</a>)</li>
                                    <li> FFmpeg (Download <a href="https://www.ffmpeg.org/download.html" target="_blank">Here</a>)</li>
                                </ul>
                                
                                <v-dialog
                                    v-model="dialog"
                                    scrollable
                                    :retain-focus="false"
                                    max-width="60vw"
                                    persistent
                                > 
                                    <template v-slot:activator="{ on, attrs }">
                                        <v-btn
                                            :color="colors[0]"
                                            class="mx-0"
                                            outlined
                                            v-bind="attrs"
                                            v-on="on"
                                        >
                                            Read More
                                        </v-btn>
                                    </template>
                                    <v-card>
                                        <v-toolbar
                                            :color="colors[0]"
                                        > 
                                            <h2>Software Installation</h2>
                                            <v-spacer> </v-spacer>
                                            <v-btn 
                                                @click="dialog = false"
                                                icon
                                            > 
                                                <v-icon> mdi-close</v-icon>
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="white black--text pt-5"> 
                                            <p>
                                                COLMAP is a general-purpose Structure-from-Motion (SfM) pipeline. This means that COLMAP can reconstruct 3D points from images taken at different angles and positions. It is open source and completely free to use. It makes use of Nvidia’s CUDA platform for certain functions, meaning that a compatible Nvidia graphics card (GPU) is required to use all functions. While MacOS is supported, since modern Mac’s don’t use Nvidia graphics cards, you will not be able to generate a full model. VisualSfM is an alternative pipeline that does not require CUDA, but it is more complex to set up and won’t be covered in this guide. 
                                            </p>
                                            <p>
                                                <b><u>Minimum Requirements:</u></b>
                                                <ul> 
                                                    <li>Windows, Mac, or Linux operating system (Windows is recommended). </li>
                                                    <li>Nvidia GPU with CUDA compute capability 3.0 or higher. </li>
                                                    <ul>
                                                        <li>Nvidia has a table <a href="https://developer.nvidia.com/cuda-gpus" target="_blank">here</a> showing which GPU’s have compute compatibility 3.0 or higher.</li>
                                                        <li>Alternatively, use GPUz (download <a href="https://www.techpowerup.com/download/techpowerup-gpu-z/" target="_blank">here</a>) to check you GPUs CUDA compute compatibility.</li>
                                                        <v-img src="https://i.imgur.com/AV3P8Wi.png" max-width="40%"> </v-img>
                                                        <li>GTX 980 or better reccomended.</li> 
                                                        <li>The most important GPU specification is video memory. COLMAP uses between 2-4GB of VRAM in our testing, which would unfortunately overwhelm most budget GPUs. More details on how to overcome this limitation later.</li> 
                                                    </ul>
                                                    <li>About 10-20 GB of storage space (Large reconstructions can take up between 5GB-10GB each).</li>
                                                    <li>At least 8GB RAM (16GB recommended).</li> 
                                                </ul>
                                                
                                            </p>
                                            <p> 
                                                <b><u>Installation Instructions:</u></b>
                                                <ol>
                                                    <li> 
                                                        <p>Download COLMAP (This guide uses COLMAP v3.6)</p>
                                                        <p> 
                                                        If you are on Windows or MacOS, download and unzip the corresponding zip file for your operating system and graphics card: https://github.com/colmap/colmap/releases 
                                                        <ul>
                                                        <li>If you are running Mac download the COLMAP-3.6-mac-no-cuda.zip.</li>
                                                        <li>If you are running Windows and have a compatible CUDA GPU (recommended), download COLMAP-3.6-windows-cuda.zip.</li>
                                                        <li>If you are running Windows but do not have compatible CUDA GPU, download COLMAP-3.6-windows-no-cuda.zip.</li>
                                                        </ul>
                                                        If you are running Linux, you will have to build COLMAP from its source code. Detailed instructions for Ubuntu are on COLMAPs install page <a href="https://colmap.github.io/install.html" target="_blank">here</a>.
                                                        </p>
                                                    </li>
                                                    <li> 
                                                        <p>Download and Install CloudCompare</p>
                                                        <p>To install CloudCompare, simply download the “installer version” from their <a href="https://www.danielgm.net/cc/" target="_blank">Downloads Page</a> and run the installer. We recommend choosing the latest stable release.</p>
                                                        <v-img src="https://i.imgur.com/rafAT3z.png" max-width="100%"></v-img>
                                                        <v-img src="https://i.imgur.com/sYBJxBf.png" max-width="80%" class="mb-3"></v-img>
                                                    </li>
                                                    <li> 
                                                        <p>Download and Install FFmpeg (Optional)</p>
                                                        <p>FFmpeg is a popular, free multimedia processing framework. If you plan on using video footage instead of images to reconstruct objects, FFmpeg will be needed to easily and quickly extract video frames at images. You could alternatively use any other software to extract video frames, but we will be using FFmpeg in this guide. </p>
                                                        <p>To install FFmpeg you can either download the source code and compile it yourself, or you can use one of their pre-complied executable files. Both are available on their <a href="https://www.ffmpeg.org/download.html" target="_blank">Download Page</a>.</p>
                                                        <p>
                                                            Here are some installation guides for Windows systems:
                                                                <ul>
                                                                    <li><a href="http://blog.gregzaal.com/how-to-install-ffmpeg-on-windows/" target="_blank">http://blog.gregzaal.com/how-to-install-ffmpeg-on-windows/</a></li>
                                                                    <li><a href="https://windowsloop.com/install-ffmpeg-windows-10/" target="_blank">https://windowsloop.com/install-ffmpeg-windows-10/</a></li>
                                                                </ul>
                                                        </p>
                                                        <p>
                                                            Here are some installation guides for Windows systems:
                                                                <ul>
                                                                    <li><a href="https://github.com/fluent-ffmpeg/node-fluent-ffmpeg/wiki/Installing-ffmpeg-on-Mac-OS-X" target="_blank">https://github.com/fluent-ffmpeg/node-fluent-ffmpeg/wiki/Installing-ffmpeg-on-Mac-OS-X </a></li>
                                                                    <li><a href="https://superuser.com/questions/624561/install-ffmpeg-on-os-x" target="_blank">https://superuser.com/questions/624561/install-ffmpeg-on-os-x </a></li>
                                                                </ul>
                                                        </p>
                                                        <p>
                                                            On Ubuntu (or any Debian-based distro) you can simply run:<br/>
                                                            <code class="ml-5"> sudo apt update <br/></code>
                                                            <code class="ml-5"> sudo apt install ffmpeg</code>
                                                        </p>
                                                        <p>
                                                         You can confirm that FFmpeg is working properly by simply typing <code>ffmpeg</code> into the command window in Windows, or the terminal in MacOS/Linux. You should see FFmpeg return some information about the current installed version. If you are on Windows and this does not work, check that you have added ffmpeg to the environment path variable (see FFmpeg guides above).
                                                        </p>
                                                        <v-img src="https://i.imgur.com/uK0GGTZ.png" max-width="100%"></v-img>
                                                    </li>
                                                </ol>
                                            </p>
                                            
                                        </v-card-text>
                                    </v-card>
                                </v-dialog>
                            </v-card-text>
                        </v-card>
                    </v-timeline-item>
                
                    <v-timeline-item
                        :color="colors[1]"
                        icon="mdi-clipboard-text-search-outline"
                        fill-dot
                    >
                        <v-card
                            :color="colors[1]"
                            dark
                        >
                            <v-card-title class="title">
                            Selecting a Model
                            </v-card-title>
                            <v-card-text class="white black--text pt-2">
                            <p>
                            In this step, you will choose a subject for your 3D model. Although some objects or structures may be easier to reconstructed based on their properties, 
                            feel free to experiment with various subjects based on your project’s requirements! 
                            </p>
                            <p>Here are some considerations before you get started:</p>
                             <v-expansion-panels light accordion multiple>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        1.  Isolated vs Non-isolated Object
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                        Your subject can either be an isolated object or a non-isolated object. 
                                        <ul> 
                                            <li>An isolated object refers to an object that is separate from its environment, such as a vase of flowers or a statue in the park. </li>
                                            <li>A non-isolated object is an object that cannot be isolated from its environment, such as a living room or a chair in the corner of a room.</li>
                                        </ul>
                                        </p>
                                        <p>In general, both subject types can generate equally precise 3D models. However, during data collection, it may be easier to collect images from different perspectives for an isolated object compared to a non-isolated object. Additionally, a model of a non-isolated object will likely contain unwanted data and will therefore take up more storage space than strictly necessary.</p>
                                        <p>Also, while it is recommended that the data collection is done on a stationary object, it is possible to reconstruct a moving object. Moving isolated objects can be reconstructed if its shape remains constant and there is enough overlap between images. On the other hand, reconstructing a moving non-isolated object is much more difficult since the software will fail to model a moving object in a static environment.</p>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        2.  Object Size
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                        It is possible to successfully reconstruct an object of any size, so long as the images taken of the object are of sufficient quantity and quality. However, keep in mind that the data collection process for larger objects is more complicated for two reasons:
                                        <ul> 
                                            <li>Generally, you will want to vary the size of the subject across your images, making the object fill the entire image or making the object occupy only a portion of the image. For larger subjects, changing the size of the object within the camera’s viewfinder requires you to move longer distances, usually closer or further away from the target.</li>
                                            <li>Taking images at different perspectives (i.e. camera angles) for a larger object also requires moving longer distances around the subject. For very tall objects, taking images at a downward angle may be impractical, which may cause the upward-facing portions of the subject to be less accurately modelled.</li>
                                        </ul>
                                        </p>
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                             <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        3. Object Texture
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                        The texture of a subject may affect what quality of model can be generated. 
                                        <ul>
                                            <li>Objects with a smooth and reflective surface tend to appear different in images based on the lighting condition and camera’s viewing angle.</li> 
                                            <li>Objects with a matte and non-reflective texture will have a more consistent look between your photos, making the reconstruction process more reliable.</li> 
                                        </ul>
                                        </p>
                                        <p>Based on your object’s surface properties, you may need to experiment with the object’s lighting conditions, environment, and more. </p>
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                             <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        4. Object Appearance
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>For the photogrammetric process to generate the best model quality, it must be able to distinguish different features of an image, such as a building corner. For subjects which have one solid color or have a consistent pattern, the software is not able to distinguish the subject’s features, causing the model generation to struggle. As a result, it is recommended that objects with easily identifiable, changing color, shape, and pattern are modelled. </p>
                                        <p>Alternatively, additional ‘targets’ may be attached to a problem subject help the software distinguish between various locations on the subject’s surface. This can be as simple as adding multiple ‘x’ shaped duct tape targets to the object’s surface.</p>
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                             <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        5. Object Location
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>To make sure that the images collected for a subject is of sufficient quality and quantity, the subject’s lighting conditions, availability, and environment must be considered. For an outdoor object, the data collection must ideally be done when there is natural lighting. For a famous statue inside a building, the data collection may only be feasible at certain times due to exhibit closing hours and user traffic. Finally, for certain immovable objects located in unstable environments, you may be limited with what camera angles and distances can be used to take images.</p>
                                        <p>Note that while this manual covers the photogrammetric process using mobile phone images, a similar process can be done using images collected online. For this method, choosing a famous or well-photographed object is ideal to ensure enough images can be collected.</p>
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                            </v-expansion-panels>
                            </v-card-text>
                        </v-card>
                    </v-timeline-item>

                    <v-timeline-item
                        :color="colors[2]"
                        icon="mdi-cellphone"
                        fill-dot
                    >
                        <v-card
                            :color="colors[2]"
                            dark
                        >
                            <v-card-title class="title">
                            Data Collection
                            </v-card-title>
                            <v-card-text class="white black--text pt-2">
                            <p>
                                Now that you've selected your model, you can start collecting your data! If you want to practice, you can use choose from some of our data sets in the 'Examples' page. Here is a basic checklist for you to follow:
                            </p>
                            <v-expansion-panels light accordion class="pb-3" multiple>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        1.	Choose a camera for data collection
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                            Any smartphone should be fine but of course the higher quality of the camera, the higher quality of the model. If you have multiple cameras available, here are some considerations when deciding between them.
                                            <ul>
                                                <li><i>Resolution</i> – Higher resolution will generally lead to better model quality, since the program can discern a greater level of detail from images.</li>
                                                <li><i>Frame Rate</i> – Higher frame rate will reduce motion blur for extracting video frames, increasing model quality.</li>
                                                <li><i>Optical Image Stabalization (OIS)</i> – Camera modules with built in OIS will generally reduce image blurriness from camera movement during capture. Note that while OIS is nice, it is not necessary to generate a good model.</li>
                                            </ul>
                                        </p>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        2.	Create a plan for your data collection
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p><pre>   "By failing to prepare, you are preparing to fail." <i>- Benjamin Franklin</i></pre></p>
                                        <p>First things first, you should decide whether or not you want to record a video or take individual images.</p>
                                        <v-expansion-panels class="mb-3">
                                        <v-expansion-panel>
                                            <v-expansion-panel-header>Video Recording vs Taking Individual Images</v-expansion-panel-header>
                                            <v-expansion-panel-content>
                                                <p>
                                                    it is recommended that you take a video of the subject instead of taking individual images. Taking a continuous video and extracting image frames from the video yields a few advantages:
                                                    <ul>
                                                        <li>Photogrammetric reconstruction usually requires a large number of images to generate a model, ideally > 50 images (depending on the subject conditions). Taking a video can save time getting to the target number of images, compared to taking photos one at a time.</li>
                                                        <li>Similarly, having the ability to extract frames from a continuous video can let you obtain images that are closer together (i.e., have more overlap). Overlap refers to how much each image shares the same content as the next image. With a video, you can adjust how frequently you’d like to extract a frame, ensuring you have enough overlap for reconstruction.</li>
                                                    </ul>
                                                </p>
                                                <p>
                                                    The video recording route also has some things you should consider:
                                                    <ul>
                                                        <li>Extracting frames from video requires additional processing time. This includes the need to experiment with different frame sampling intervals to get the best possible images.</li>
                                                        <li>Motion blur may lower the quality of your model. To minimize motion blur try:</li>
                                                        <ul>
                                                            <li>Moving the camera slowly during recording or stay stationary for a few seconds before changing location.</li>
                                                            <li>When extracting images, try changing the sampling rate based on how often you moved the camera.</li>
                                                            <li>Using a camera capable of recording at a higher frame rate. </li>
                                                            <li>Using a camera with optical image stabilization (OIS) or a manual image stabilization method (e.g. gimbal mount, selfie stick).</li>
                                                        </ul>
                                                    </ul>
                                                </p>
                                            </v-expansion-panel-content>
                                        </v-expansion-panel>
                                        </v-expansion-panels>
                                        <p><i>Note: Data collection can also be done by collecting images of a subject online. The process will not be covered here, but the same principles apply.</i></p>
                                        <p>Once you've decided, here are some tips/ things to consider for a successful data collection:
                                            <ol>
                                                <li>Determine the best way to shoot the video to cover as much of the subject as possible. If your subject is just one side of a building, then choose which side of the building you will start at and determine a route around building face.</li>
                                                <li>Set a goal for the number of images or video length you require. The video duration should depend on the size of the subject. More is always better! When in doubt, shoot more images and/or record longer videos.</li>
                                                <li>Plan to bring along any additional equipment to improve the data collection. Some examples include:</li>
                                                <ul>
                                                    <li>A stand/pedestal to elevate a smaller object off the ground.</li>
                                                    <li>A selfie stick for increasing stability.</li>
                                                    <li>A lamp/flashlight to illuminate the subject.</li>
                                                </ul>
                                            </ol>
                                        </p>
                                        <p><i>Note: Optionally, bring a ruler/tape measure and physically measure the dimensions of your object. You can use these measurements to compare with the measurements from the 3D model to determine model accuracy.</i></p>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        3.	Perform the data collection
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                            When doing data collection, try following some of these tips:
                                            <ul>
                                                <li>When taking video, move slowly to reduce motion blur and increase image overlap.</li>
                                                <li>Take images in portrait and landscape mode (rotate the camera slowly if you're taking a video or take pictures while rotating the phone). </li>
                                                <li>Remember, when in doubt, shoot more images and/or record longer videos! You won't be sorry you did.</li>
                                            </ul>
                                        </p>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>                             
                            </v-expansion-panels>
                            <p>Once you got all the images/ videos you need, transfer them to your computer and you're ready to move on!</p>
                            </v-card-text>
                        </v-card>
                    </v-timeline-item>
                    <v-timeline-item
                        :color="colors[3]"
                        icon="mdi-laptop"
                        fill-dot
                    >
                        <v-card
                            :color="colors[3]"
                            dark
                        >
                            <v-card-title class="title">
                            Pre-Processing (For Videos Only)
                            </v-card-title>
                            <v-card-text class="white black--text pt-2">
                                <p>Taking videos is the recommended data collection method over taking individual images. But COLMAP cannot accept video files directly, so we must first use FFmpeg to extract some video frames for COLMAP to process.</p>
                                <p>If you collected individual images, then there is no preprocessing necessary. You can look through and remove bad images (blurry, bad lighting, etc) if you like, but COLMAP generally does a pretty good job with removing low quality images on its own. </p>
                            <v-dialog
                                    v-model="dialog2"
                                    scrollable
                                    :retain-focus="false"
                                    max-width="60vw"
                                    persistent
                                > 
                                    <template v-slot:activator="{ on, attrs }">
                                        <v-btn
                                            :color="colors[3]"
                                            class="mx-0"
                                            outlined
                                            v-bind="attrs"
                                            v-on="on"
                                        >
                                            Read More
                                        </v-btn>
                                    </template>
                                    <v-card>
                                        <v-toolbar
                                            :color="colors[3]"
                                        > 
                                            <h2>Pre-Processing</h2>
                                            <v-spacer> </v-spacer>
                                            <v-btn 
                                                @click="dialog2 = false"
                                                icon
                                            > 
                                                <v-icon> mdi-close</v-icon>
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="white black--text pt-5"> 
                                            <p>For this step you will need to have FFmpeg installed. If you do not, please follow our installation guide in the 'Software Installation' Module.</p>
                                            <p>
                                                <b><u>Steps:</u></b>
                                                <ol>
                                                    <li>Create a subfolder called images in the same directory as your video file.</li>
                                                    <li>Open Command Prompt (Windows) or Terminal (Mac/Linux)</li>
                                                    <li>
                                                        <p>Extract images using FFmpeg. You can use the following code in the Command Prompt/ Terminal:</p>
                                                        <p><code>ffmpeg -i "video.mp4" -r 1 images/image%03d.png</code></p>
                                                        <p>Replace<code>"video.mp4"</code>with the name of your video file. The<code>"-r 1"</code>specifies a framerate of 1, meaning 1 image will be extracted for every 1 second of the video. We recommend extracting approximately 100 images from you video for reconstruction. 
                                                            This means that the framerate should be set to 100 divided by the length of your video in seconds.<code>"images/image%03d.png"</code> specifies the subdirectory and filename of the extracted images.
                                                        </p>
                                                    </li>
                                                </ol>
                                            </p>
                                        </v-card-text>
                                    </v-card>
                             </v-dialog>
                            </v-card-text>
                        </v-card>
                    </v-timeline-item>
                    <v-timeline-item
                        :color="colors[4]"
                        icon="mdi-printer-3d"
                        fill-dot
                    >
                        <v-card
                            :color="colors[4]"
                            dark
                        >
                            <v-card-title class="title">
                            3D Reconstruction with COLMAP
                            </v-card-title>
                            <v-card-text class="white black--text pt-2">
                                <p>Now that a set of images is ready to process, COLMAP is used for the 3D reconstruction. This tutorial will focus of COLMAP’s automatic reconstruction feature. COLMAP has much more in-depth documentation and troubleshooting information on their <a href="https://colmap.github.io/" target="_blank">GitHub</a>.</p>
                            <v-dialog
                                    v-model="dialog3"
                                    scrollable
                                    :retain-focus="false"
                                    max-width="60vw"
                                    persistent
                                > 
                                    <template v-slot:activator="{ on, attrs }">
                                        <v-btn
                                            :color="colors[4]"
                                            class="mx-0"
                                            outlined
                                            v-bind="attrs"
                                            v-on="on"
                                        >
                                            Read More
                                        </v-btn>
                                    </template>
                                    <v-card>
                                        <v-toolbar
                                            :color="colors[4]"
                                        > 
                                            <h2>3D Reconstruction with COLMAP</h2>
                                            <v-spacer> </v-spacer>
                                            <v-btn 
                                                @click="dialog3 = false"
                                                icon
                                            > 
                                                <v-icon> mdi-close</v-icon>
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="white black--text pt-5"> 
                                            <p>For this step you will need to have COLMAP installed. If you do not, please follow our installation guide in the 'Software Installation' Module.</p>
                                            <p>
                                                <b><u>Steps:</u></b>
                                                <ol>
                                                    <li>Open the COLAMP graphical interface (Run the COLMAP.bat file on Windows, COLMAP.app on MacOS, or execute colmap gui in a linux terminal).</li>
                                                    <li>Click on Reconstruction -> Automatic reconstruction.</li>
                                                    <v-img src="https://i.imgur.com/4G0aONh.png" max-width="70%" class="my-3"></v-img>
                                                    <li>Enter a directory in “Workspace folder” for the COLMAP project (including the finished models).</li>    
                                                    <li>Enter the directory containing all your images in “Image folder”.</li>    
                                                    <li>Choose a “Data Type”.</li> 
                                                    <ul>
                                                        <li>Individual images is the default and suggested setting. It attempts to match every image to every other image exhaustively. It is more time consuming but also the most reliable.</li>
                                                        <li>Video frames assumes that the images are ordered and follow the same path. This helps reduce processing time, since images are only matched with neighboring images. But if your video moves too quickly (from a fast panning move, for example) COLMAP may not be able to match some sequential images.</li>
                                                        <li>Internet images optimizes for low quality images. It is more robust than the other data types but may introduce far more noise into the final model.</li>
                                                    </ul>   
                                                    <li>Choose a "Quality Setting". The higher the quality setting, the more time COLMAP will spend trying to extract features and remove outliers. The High setting is recommended.</li>
                                                    <li>"Shared intrinsics" should be enabled if all images were recorded with the same camera. It speeds up processing time by assuming that all images were taken by cameras with the same intrinsic properties such as focal length and lens distortion.</li>
                                                    <li>"Sparse model" should always be enabled. This generates a model with a low number of points. The dense reconstruction in the next step builds off this spares model.</li>
                                                    <li>"Dense model" enables dense reconstruction. This step requires a compatible Nvidia GPU (see Installing Software Requirements). The GPU box must be checked for this step.</li>
                                                    <li>"Num_threads" specifies the number of CPU threads COLMAP should use. The default value of -1 allocates one thread for each CPU core. Reducing the number of threads will cause COLMAP to run much slower, but may also allow you to do other things on your computer while COLMAP is running. </li>
                                                    <li>"gpu_index" specifies which GPU COLMAP should use. This only needs to be set if you have multiple graphics processors (such as a laptop with both integrated and dedicated graphics processing).</li>
                                                    <li>Click Run and grab a snack, it could take a while! If you would like to read the log as the adjustment is running, you might want to resize the log panel on the right of COLMAP’s GUI before pressing run since the panel cannot be resized while COLMAP is running.
                                                        If you have dense reconstruction enabled, this will likely take one or more hours.
                                                    </li>                                          
                                                </ol>
                                            </p>
                                        </v-card-text>
                                    </v-card>
                             </v-dialog>
                            </v-card-text>
                        </v-card>
                    </v-timeline-item>
                </v-timeline>
            </v-col>
        </v-row>
    </v-container>
</template>

<script>
export default {
  name: 'manual',

  data: () => ({
    colors: ['teal darken-1', 'blue darken-1', 'indigo darken-1', 'purple darken-1', 'deep-purple darken-1'],
    dialog: false,
    dialog2: false,
    dialog3: false,
  }),
  mounted() {
      window.scrollTo(0, 0);
  }
};

</script>