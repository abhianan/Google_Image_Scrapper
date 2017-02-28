# Google Image Scrapper and Downloader

Approach used in this project is same as Anthony Casagrande and can be obtained from https://github.com/BirdAPI .
This project will help you in Scraping https://images.google.com/ . 

#####Image downloading Functionality added

##Demo
For Demo of only scraping use the code

```python
	from Google-Image-Scrapper import google
	s=raw_input("Enter Your Query ")
	results = google.search_images(s)
	for img in results:
    	p=str(img).split(',')
    	fpic=p[len(p)-1][:-1][6:]
    	print fpic
```
For Demo of Downloading images use the code

```python
	from Google_Image_Downloader import google,images
	s=raw_input("Enter Your Query ")

	options = images.ImageOptions()
	options.larger_than = images.LargerThan.VGA
	results = google.search_images(s,options)
	images.fast_download(results, path =s, threads=12)
```

###Other Approach
======
This approach will grab small only small size pic
```python
	from bs4 import BeautifulSoup
	import mechanize


	def imget(si):
			 try:
					br=mechanize.Browser()
					br.set_handle_robots(False)
					br.addheaders=[('User-Agent','Mozilla')]
					img=br.open("https://www.google.com/search?site=&tbm=isch&source=hp&biw=1280&bih=899&q="+si+"&oq="+si)
					soup=BeautifulSoup(img)
					result=soup.findAll('img')

					for i in result:
							print i["src"]

			except:
					print "No result"

	pimage=raw_input("Enter the name of object \n")
	imget(pimage)
```
