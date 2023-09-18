
Technology is always adapting, which can be both a blessing and a curse. In our case, it proved to be the latter. We decided to pick up SimplyClip as the project we would be running as part of our project1. SimplyClip 3.0 is a chrome extension, that provides a user a shared clipboard. Using it, they do not have to switch tabs/windows to paste their copied content. They simply need to select the text and the tool will clip it for them. It also comes with a host of other functionalities like merging text, ordering the text, summarising it, exporting the text to doc/csv, etc. Now all this makes it a very useful tool but the last version of it was made in 2021, thus, the technology used in it was a bit outdated. The maintenance and support to some libraries and tools used in it being revoked.
Following, we will be jotting down the process as to how we were finally able to get it running:

•	It is a chrome extension; thus, we just need to zip the code from the repository and load the unpacked extension to run it.

•	When we did this, the extension was loading but we were unable to copy any data and the extension was crashing even before we tried to use it.

•	Upon further investigation, we figured out that the error was "Cannot read property 'addEventListener' of null ". This error resulted as the extension was trying to access the content of the webpage, before it was ever loaded.

•	To fix this, we added a code snipped which would wait for the DOMContentLoaded to complete, before trying to access any data from the webpage.

•	This seemed to have done the trick and we were able to proceed further. But again, we ran into an issue where we were unable to actually copy the text just by selecting it.

•	This functionality was the core of SimplyClip and its major selling point, where a user did not have to manually copy and paste the text. 

•	After reviewing the code, we figured out that there was a specific order in which we have to perform the tasks for the extension to work.

•	This does make sense from the point of view of how the extension works, but this exact methodology must have been documented, such that a new user is able to pick up on how to use the extension correctly from the get go.

•	Another issue that we ran into after this was that there is a limit on the size of text that we can select while using SimplyClip. This size limit requirement also was not mentioned and it took us quite a while to figure out why we were able to copy certain text paragraphs and not others.

•	Then, we ran into an issue where the exporting to doc was not working. There was no issue with csv export but only doc.

•	The reason for this was that, we had text summarization functionality associated with the exported doc file. This means that if we wanted to summarize some text, the summarizer code that was being triggered to remove stop words and redundant sentences would summarize the text and return the output in a document. 

•	As this summarizer itself was not working, the document export part was failing as well.

•	To correct this, we had to look into the backend dependencies of the various libraries downloaded.

•	We had downloaded the requirements that were mentioned in the repository but still there were dependency issues among various modules.

•	We had to install the correct versions of Django and G mocha, post which this functionality was working correctly.

After successfully performing all these steps, we were able to run our extension. This process was quite tedious and we had to go through a lot of trial and error to finally figure out the correct methodology to get it to function as expected. Following are a few points that we must keep in our mind such that we can avoid such issues in the future:

•	The code repository must be regularly checked to see if there is any module whose support has been discontinued. It is not possible to do it in project that will be discontinued post a semester but we can do it some justice, by seeing what all modules are suspected to be discontinued or revamped soon.

•	If this is done while planning the project, then it will prevent a lot of such basic run and configuration issues.

•	Moreover, for a developer, they know how their code/project works and therefore, they tend to look over documenting certain details of their project, which they consider to be trivial.

•	Later, all these undocumented minute details are the ones which cause issues for a new developer who picks up the project or an end-user who is using this application for the very first time.

•	This will save a lot of time and resources for a new developer, and for a new user, it will make it much easier for them to understand the application, how it works and encourage to use it again.

•	Again, the requirements that worked for the previous developers might not work for a new developer at a later point of time, the reason being technology having changed, libraries/modules discontinued, support to them dropped, etc. 

•	Thus, to maintain these applications, these dependencies must be regularly checked to see if there are any discrepancies with any of the modules.

Following are a few practices which we will be committing to, to avoid issues like the ones mentioned above:

•	We will be documenting all the details necessary to run and maintain our application and also all the changes we made on top of the codebase.

•	We will get into the shoes of a naïve first-time user and document all things that are necessary for such a user to be able to make the best out of SimplyClip.

•	We will also be doing a due diligence on what modules/libraries we have used and if there are any that are being discontinued in recent future. If so, we will try to replace them with more sustainable and scalable alternatives.

•	Lastly, we will make sure that we provide clear, concise and easy to comprehend documentation regarding all changes we make to the original project.
