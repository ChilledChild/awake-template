---
title: Introduction to Autopsy
subtitle: The first byte of digital forensics
category:
  - Digital Forensics
author: Danny Child
date: 2021-04-06T05:30:00.000Z
featureImage: /uploads/autopsy_wide.png
---
[Autopsy](https://www.autopsy.com/) is an open-source digital forensic tool that allows for manual inspection of a static digital image. While it can be combined with the [Sleuth Kit](https://sleuthkit.org/), Autopsy focuses on identifying and retrieving files from a digital image. Autopsy is used by forensic analysts who work for security companies, police departments, even within an organization’s IT group. Multiple data sources can be combined into generated reports used for investigations as forensic evidence.

## **Preparing for an investigation**

Forensic cases require intense and precise levels of documentation to ensure that evidence is handled correctly. Upon starting a new case, Autopsy offers to record a case number, case examiner contact, and listed organizations. These values are pre-determined by the person leading the investigation, with a secondary person performing the analysis.

Each case is a database that can contain multiple data sources. Autopsy can read a local disk (like the E drive), a VM file, disk image, and other logical files. After specifying a file path, time zone, and appropriate values, the data will load and be ready for analysis. Additional data sources can be added after a case is started.

## **Investigating the filesystem**

### **Directory Tree**

On loading a data source for investigation, the left side shows a tree of results that contains all parts of the investigation. Each data source is listed by drive, whose contents can be searched as a directory or in groups of notable attributes. Not only are unique files identified, information about the operating system, its users, metadata, and deleted files can be found here as well. This can prove useful for cases where time spent investigating is cut short, so important items can be quickly accessed.

### **List Details**

The right side shows the detailed view of the directory, under the listings tab. This section will typically include creation and modified timestamps, file location, size, and extension. This window appearance can be swapped between a table and thumbnail view. Filters can be applied to narrow a search for keywords, extensions, modifiable regex filters.
Selecting files will display additional data in the lower section including hex values, strings, generated images, and metadata values. For .lnk (shortcut) files, the results tab will show the source file path that the .lnk file refers to and can be immediately accessed by right-clicking on the listed path.

At any given point, a file or directory can be extracted to be analyzed with separate tools. By right-clicking on a file or folder while in the directory listing will export it to the default case path directory under the Export folder, or any chosen file path.

### **Tagging notable items**

Any identifiable item in Autopsy can be tagged for reporting. Marking items as notable, to follow up, or with a degree of child exploitation, both “illegal” and “CGI/animation” based. Child exploitation cases were accounted for when creating Autopsy, so these categories are natively included. Custom tags can be assigned if the investigation does not relate to adult content.

### **Creating a timeline of significant events**

The Timeline button in the navigation bar opens a new window that will show all items in relation to when they were interacted with. The display can be filtered by time, file type, file size, location, even contained strings. The display view can be swapped between the count of events, a detailed timeline, or list of events. The presented files will be sorted and stacked based on time and where they reside in the image. Selecting a file or group of files in the timeline will show the details in the lower half of the window.

While in the Details View mode, selected files or groups can be pinned to the top window for later search or to a final report. Custom events which may have occurred outside of the digital world can be added to the timeline, such as physically moving the machine or when specific people were in front of the computer. Markers can be placed as reference points in the timeline. While having forensically sound evidence is required for any investigation, presenting the data in a way that explains the context and reasoning behind a statement is just as important. Using the snapshot feature will save what is seen in the timeline as an html report.

### **Mapping communications**

Autopsy can identify communication that was recorded on a disk. The Communications button opens a new window containing a list of recorded accounts sending and receiving communication traffic. Results can be filtered by type of communication, data sources, and date range. This can be visualized when right clicking an account and selecting “Add Selected Account to Visualization”. The right side of the window will show a summary of messages, attachments, and where each can be found in the directory listing. Email files can be read directly by selecting the messages tab, viewing individual emails, threads, headers, and attachments.

The Visualization tab shows a map of recorded communication, including the sender and recipient. Multiple contacts can be selected to filter the visualization. Selecting “Snapshot Report” when in the Visualize tab will record an HTML file that includes an image of the visible graph. Case information and select metadata regarding the graph will be recorded in the report.

### **Generating reports**

Detailed reports can be generated from the directory listing, timeline tab, and communication tab. Generating a report while in the directory listing will provide options for the report format. Outputted results will vary based on the format, though data can be filtered based on tagged results, geolocated tagged events, even compared against a list of hashes or [STIX](https://oasis-open.github.io/cti-documentation/stix/intro) files.

The Timeline search can record a screenshot of the timeline results window. An HTML file will be generated that includes details about the overall case, along with the timeline snapshot and time range. The Communications search can record a screenshot of the mapped communications visualization. These should be used as a supplement to other reports so event details can be understood from a timeline and endpoint perspective. The primary report provides details on identified files, and should lead the case documentation.

## **Putting Autopsy in practice**

I learned how to use Autopsy from training material provided in [Security Blue Team](https://securityblue.team/)’s BTL1 certification, and [BTLO](https://blueteamlabs.online/) pro labs. While affordable training is available, there is also free training from other sources. [DFIR Diva](https://dfirdiva.com/) has lists of free and affordable trainings that focus on digital forensics. [Digital Corpora](https://digitalcorpora.org/) has a collection of disk images and scenarios with answers provided. Becoming familiar with Autopsy and forensic investigation methods will take time and practice. Read the official [Autopsy user documentation](https://sleuthkit.org/autopsy/docs/user-docs/) to see additional guides and topics.