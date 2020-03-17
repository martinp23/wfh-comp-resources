## Things to do for isolated research students

- [Editorials and other information](#editorials-and-other-information)
- [NSW/UNSW-specific information](#nsw-unsw-specific)
- [Video-conferencing tools](#video-conferencing-tools)
- [Reading](#reading)
- [Learn python](#learn-python)
- [Learn bash/shell](#learn-bash-shell)
- [Play with some computational chemistry](#play-with-some-computational-chemistry)
- [Learn machine-learning and data science](#learn-machine-learning-and-data-science)
- [Learn something else new](#learn-something-else-new)
- [Get on top of administration and data analysis](#get-on-top-of-administration-and-data-analysis)
- [Sources/acknowledgements](#sources-acknowledgements)
- [Other pages on this site](#sitemap)

This short document lists possible activities suitable for Honours and HDR candidates who are working from home as part of social distancing, or who are asymptomatic and self-isolating. If you're unwell, you should rest. In any case, you should not expect to be as productive as usual - this is a very stressful and uncertain time. The goal of this document is to give you some things to do, and some structure, in case that will help you.

### Editorials and other information
- [Here's an editorial from Science about isolation](https://www.sciencemag.org/careers/2020/03/working-home-because-covid-19-here-are-10-ways-spend-your-time)
- A good twitter thread on [setting up a routine](https://twitter.com/WildBrisco/status/1239601642972033032)
- Exercise: if safe (i.e. you're not sick), and not prohibited by authorities, take a walk/run around the block. Treat it as your 'commute'. Look into other exercise you might be able to do without access to a gym. 

### NSW/UNSW-specific 
- [NSW Health COVID-19](https://www.health.nsw.gov.au/Infectious/diseases/Pages/coronavirus.aspx)
- [UNSW COVID-19](https://www.unsw.edu.au/advice-on-unsw-response-to-the-coronavirus)
- [UNSW Health COVID-19](https://student.unsw.edu.au/health-service-information-coronavirus#overlay-context=hsu)
- [UNSW library instructions for off-site access](https://www.library.unsw.edu.au/study/access-to-online-resources)
- Accessing journals through the UNSW library proxy: insert this into the URL: .wwwproxy1.library.unsw.edu.au between the domain and the path, then log in. For example: [https://www.nature.com.wwwproxy1.library.unsw.edu.au/articles/s41586-020-2068-4](https://www.nature.com.wwwproxy1.library.unsw.edu.au/articles/s41586-020-2068-4). Here are [instructions to make a button for your bookmark bar which automatically reloads a page using the proxy](make-lib-bookmarklet.md).


### Video-conferencing tools

- [Zoom](https://zoom.us): free for up to 40 mins for meetings; unlimited 1:1s. [UNSW link](https://www.myit.unsw.edu.au/services/staff/software/zoom-conferencing).
- [Teams](https://products.office.com/en/microsoft-teams/work-remotely) ([UNSW teaching page](https://teaching.unsw.edu.au/digital-assessment-toolkit/microsoft-teams))
- Skype
- VPN access ([UNSW link](https://www.myit.unsw.edu.au/services/students/remote-access-vpn))

### Reading

Use this opportunity to get up to date with the literature. Here are a few ways to do this:

- You can use [Kopernio](https://kopernio.com) to access many papers available through your institution library from home. UNSW students, see UNSW-specific section above for more info.
- Follow RSS feeds of top journals using a cloud feed reader like [feedly](https://feedly.com/). Suggested journals include [Nature Chem](https://www.nature.com/nchem/), [JACS](https://pubs.acs.org/journal/jacsat), [Angew Chem](https://onlinelibrary.wiley.com/journal/15213757), [Chem Sci](https://pubs.rsc.org/en/Journals/JournalIssues/SC#!recentarticles&adv)
- Do keyword searches for useful reviews and articles on [web of science](https://webofknowledge.com) and [google scholar](https://scholar.google.com/)
- Set up Google Scholar alerts for keywords (or people) relevant to your project
- Do a short literature review (in consultation with me - you don't be on your own with this!)

### Learn python

- Learn python: [codeacademy.com](https://codeacademy.com) or [Datacamp for students](https://www.datacamp.com/github-students). Note that the Datacamp-Github student pack gives you 3 months free premium access. This could be great opportunity to use it to learn Python (and bash/shell, see below). The [Github student pack](https://education.github.com/pack) includes a lot of other free stuff for students - make the most of it!
- Flick through this book on Python Computations in Science and Engineering to see what's possible: [https://kitchingroup.cheme.cmu.edu/pycse](https://kitchingroup.cheme.cmu.edu/pycse/)
- Learn how to plot data in python: [https://matplotlib.org](https://matplotlib.org)
- Consider installing Anaconda (a python distribution) on your computer
- Learn python for scientists with this EdX course: [https://online-learning.harvard.edu/course/using-python-research](https://online-learning.harvard.edu/course/using-python-research)
- The best way to learn is to have a project. Maybe try re-analysing some experimental data

### Learn bash/shell

- Bash is a unix shell language and you will use if it you ever do high-performance computing
- You can read about the main commands here: [https://www.freecodecamp.org/news/the-best-linux-tutorials/](https://www.freecodecamp.org/news/the-best-linux-tutorials/)
- This video shows tutorial examples [https://www.youtube.com/watch?v=BFMyUgF6I8Y](https://www.youtube.com/watch?v=BFMyUgF6I8Y)
- If you get a free Datacamp subscription, you can use that to [learn bash](https://www.datacamp.com/courses/tech:shell).

### Play with some computational chemistry

- You can run many tools on a Windows or UNIX system. Otherwise, you should use a high-performance computing (HPC) service such as that provided by your institute.
- If you want to run some tools on Windows, you first need to [install Windows Subsystem for Linux](install-wsl.md)
- Start with XTB, which is an open-source program for semi-empirical calculations. Download it from here and install into WSL or on unix:  [https://xtb-docs.readthedocs.io/en/latest/setup.html](https://xtb-docs.readthedocs.io/en/latest/setup.html) (NB: install the binaries. You don't need to compile from source). See [separate document for an XTB tutorial](use-xtb.md)
- You can install orca onto a Windows computer or use it on a HPC. This program allows you to do some higher levels of theory, including DFT. See [https://orcaforum.kofo.mpg.de/app.php/portal](https://orcaforum.kofo.mpg.de/app.php/portal) for download info and see separate resource for use instructions (tba)
- You can use Gaussian on our HPC. See separate document (tba).

### Learn machine-learning and data science
- [Kaggle has a range of resources and comptetitions for learning data science](https://www.kaggle.com/)
- Take a look at Vittorio Saggiomo&#39;s tweet (which inspired this document) for more: [https://twitter.com/V\_Saggiomo/status/1238776802530807809](https://twitter.com/V_Saggiomo/status/1238776802530807809)

### Learn something else new
- Consider free courses from [edx](https://www.edx.org/) or [coursera](https://www.coursera.org/).

### Get on top of administration and data analysis
- If you have access to everything you need, try to find time to get on top of your data analysis and administration tasks. You don't want to come back to study after this period with a huge todo list.
  - Data processing and filing
  - Notes on data analysis
  - Expense claims

### Sources/acknowledgements

I'm trying to build this document by taking on information from public and non-public sources. Here are particular acknowledgements:

- Vittorio Saggiomo's tweet: [https://twitter.com/V\_Saggiomo/status/1238776802530807809](https://twitter.com/V_Saggiomo/status/1238776802530807809)
- [NewPI slack](https://newpislack.wordpress.com/)
- [Dr Laura McKemmish](http://www.chemistry.unsw.edu.au/staff/laura-mckemmish) for suggestions

### Sitemap
- [Installing and using Windows Subsystem for Linux](install-wsl.md)
- [Installing and introduction to GFN-xtb](use-xtb.md)
- [Instructions to make a button for your bookmark bar which automatically reloads a page using the UNSW library proxy](make-lib-bookmarklet.md)
