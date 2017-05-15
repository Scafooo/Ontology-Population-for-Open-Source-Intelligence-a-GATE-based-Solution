![alt text](https://github.com/Scafooo/Ontology-Population-for-Open-Source-Intelligence-a-GATE-based-Solution/blob/master/images/logo.png)

# Setting Up The GATE System for OSINT Project

Authors: Giulio Ganino, Domenico Lembo, Massimo Mecella, Federico Scafoglieri

In this Section we show all the steps needed to set up our solution. We remark that what we describe in the following is not a simple collection of pieces of documentation available for GATE and the processing resources we use. Indeed, some of these resources are lacking of complete or adequate documentation, and their combination in our pipeline requires special configurations. Therefore, the instructions we list below are crucial to properly set up the environment for our aims.


## 1.1 Downloading and Installing GATE
To download GATE, point your web browser at http://gate.ac.uk/download and download the installer for GATE Developer 8.2 (∼570MB) through the selection of Generic installer for any platform. This is an executable JAR file that should run when you double click it. If this fails, runitfromthecommandlineusingjava -jar gate-8.2-build5482-installer.jar. GATE runs anywhere that supports Java 7 or later, including Solaris, Linux, Mac OS X ,and Windows platforms.


## 1.2 Loading Processing Resources

In GATE, processing resources are used to automatically create and manipulate annotations on documents. The CREOLE∗ plugins allow to use the Processing Resources (and certain language resources) provided by GATE. In the CREOLE plugin menu we can choose the plugin that contains the processing resource that we want to use. Notice that a single plugin may contain various resources, e.g., in Figure 1, we show the resources that are in the ANNIE plugin.
The CREOLE plugins can be managed through the graphical user interface which can be activated by selecting “Manage CREOLE Plugins” from the “File” menu. This will bring up a window listing all the known plugins. For each plugin there are two check-boxes, one labelled “Load Now” , which will load the plugin, and the other labelled “Load Always” which will add the plugin to the list of auto-loadable plugins. A “Delete” button is also provided, which will remove the plugin from the list of loaded plugins. This operation does not delete the actual plugin directory, so that it can be reloaded in future usages.. Installed plugins are found automatically when GATE is started; if an installed plugin is deleted from the list, it will re-appear next time GATE is launched.
In order to set up our pipeline we need to select the Load Now box in the CREOLE Plugin Manager for the following plugins:

* ANNIE, from which we take the following processing resources:
  * Document Reset
  * GATE Unicode Tokeniser 
  * RegEx Sentence Splitter
  * ANNIE Gazetteer
  * Jape Transducer
* Tagger Framework, which contains the Generic Tagger Processing Resource
* OwlExporter. To load this processing resource we need to download the creole.zip file from http://www.semanticsoftware.info/owlexporter, unzip the downloaded file, after that push the button with the symbol + in the upper-left corner of the tab “Install Plugins” (cf. Figure 1), and specify the path of the unzipped folder containing the OwlExporer resource. Finally we can flag the Load Now box in correspondence of OwlExporter in the
CREOLE Plugin Manager.


## 1.3 Configure Processing Resources

To set and run CREOLE resources, we need to go back to the GATE home page (Figure 2). By a right click on the menu “Processing Resources”, the list of the resources loaded in the previous step will be shown, so that it is possible to select the resources to be configured (in the GATE terminology this selection is called resource creation). When a specific processing resource is created, it appears as a sub-item of the menu “Processing Resources”, as we can observe in Figure 2 for the GATE Unicode Tokeniser.
Notice that it is possible to select the same processing resource more than once, and thus create more than one instance of the same resource, which however has to be assigned with a different name. This is particularly useful if the same resource will be used several times with different parameters. Below we describe how to set the initialisation parameters for each resource (run-time parameters will be set later).

**Document Reset.** For this processing resource the only parameter that can be modified is the name. In our solution we have used the default name assigned to such resource (as shown in Figure 3).
**Gate Unicode Tokeniser.** Besides the name, two other parameters can be set: rulesURL and encoding. The former contains the URL for the ruleset file, which is the file containing the rules for
