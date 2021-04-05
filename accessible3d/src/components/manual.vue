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
                                                        <v-img src="https://i.imgur.com/sYBJxBf.png" max-width="80%"></v-img>
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
                             <v-expansion-panels light accordion>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        1.  Isolated vs Non-isolated object
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                        Your subject can either be an isolated object or a non-isolated object. An isolated object refers to an object that is separate from its environment, such as a vase of flowers or a statue in the park. On the other hand, a non-isolated object is an object that cannot be isolated from its environment, such as a living room or a chair in the corner of a room.
                                        </p>
                                        <p>
                                        In general, both subject types can generate equally precise 3D models. However, during data collection, it may be easier to collect images from different perspectives for an isolated object compared to a non-isolated object. Additionally, a model of a non-isolated object will likely contain unwanted data and will therefore take up more storage space than strictly necessary.
                                        </p>
                                        <p>
                                        Also, while it is recommended that the data collection is done on a stationary object, it is possible to reconstruct a moving object so long as it is isolated, its shape remains the same, and there is enough overlap between images to perform photogrammetry. For non-isolated objects however, modelling a single moving object in a static environment will cause the model generation to fail.
                                        </p>
                                    </v-expansion-panel-content>
                                </v-expansion-panel>
                                <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        2.  Object Size
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>
                                        It is possible to successfully reconstruct an object of any size, so long as the images taken of the object are of sufficient quantity and quality. However, keep in mind that the data collection process is more complicated for larger objects:
                                        </p>
                                        <ul> 
                                            <li>For larger subjects, changing the size of the object within the camera’s viewfinder requires you to move longer distances, usually closer or further away from the target. Generally, you will want to vary the size of the subject across your images, making the object fill the entire image or making the object occupy only a portion of the image. </li>
                                            <li>Taking images at different perspectives (i.e. camera angles) for a larger object also requires moving longer distances around the subject. For very tall objects, taking images at a downward angle may be impractical, which may cause the upward-facing portions of the subject to be less accurately modelled. </li>
                                        </ul>
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                             <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        3. Object Texture
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        The texture of a subject may affect what quality of model can be generated. Objects with a smooth and reflective surface tend to appear different in images based on the lighting condition and camera’s viewing angle. On the other hand, objects with a matte and non-reflective texture will have a more consistent look between your photos, making the reconstruction process more reliable. Based on your object’s surface properties, you may need to experiment with the object’s lighting conditions, environment, and more.
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                             <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        4. Object Appearance
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>For the photogrammetric process to generate the best model quality, it must be able to distinguish different features of an image, such as a building corner. For subjects which have one solid color or have a consistent pattern, the software is not able to distinguish the subject’s features, causing the model generation to struggle. As a result, it is recommended that objects with easily identifiable, changing color, shape, and pattern are modelled. </p>
                                        <p>Alternatively, additional ‘targets’ may be attached to a problem subject help the software distinguish between various locations on the subject’s surface. This can be as simple as adding duct tape to parts of the object.</p>
                                    </v-expansion-panel-content>
                             </v-expansion-panel>
                             <v-expansion-panel>
                                    <v-expansion-panel-header>
                                        5. Object Location
                                    </v-expansion-panel-header>
                                    <v-expansion-panel-content>
                                        <p>To make sure that the images collected for a subject is of sufficient quality and quantity, the subject’s lighting conditions, availability, and environment must be considered. For an outdoor object, the data collection must ideally be done when there is natural lighting. For a famous statue inside a building, the data collection may only be feasible at certain times due to exhibit closing hours and user traffic. Finally, for certain immovable objects located in unstable environments, you may be limited with what camera angles and distances can be used to take images, which may affect model quality.</p>
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
                            
                            <v-dialog
                                    v-model="dialog3"
                                    scrollable
                                    :retain-focus="false"
                                    max-width="60vw"
                                    persistent
                                > 
                                    <template v-slot:activator="{ on, attrs }">
                                        <v-btn
                                            :color="colors[2]"
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
                                            :color="colors[2]"
                                        > 
                                            <h2>Selecting a Model</h2>
                                            <v-spacer> </v-spacer>
                                            <v-btn 
                                                @click="dialog3 = false"
                                                icon
                                            > 
                                                <v-icon> mdi-close</v-icon>
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="white black--text pt-5"> 
                                        </v-card-text>
                                    </v-card>
                             </v-dialog>
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
                            Pre-Processing
                            </v-card-title>
                            <v-card-text class="white black--text pt-2">
                            <v-dialog
                                    v-model="dialog4"
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
                                            <h2>Selecting a Model</h2>
                                            <v-spacer> </v-spacer>
                                            <v-btn 
                                                @click="dialog4 = false"
                                                icon
                                            > 
                                                <v-icon> mdi-close</v-icon>
                                            </v-btn>
                                        </v-toolbar>
                                        <v-card-text class="white black--text pt-5"> 
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
    colors: ['teal darken-1', 'blue darken-1', 'indigo darken-1', 'deep-purple darken-1'],
    dialog: false,
    dialog2: false,
    dialog3: false,
    dialog4: false,
  }),
  mounted() {
      window.scrollTo(0, 0);
  }
};

</script>