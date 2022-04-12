# SwordBox
//.......//
import requests 
from bs4 import BeautifulSoup as bs

def get_urls(target):
    headers = {"User-Agent":"Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/63.0.3239.132 Safari/537.36"}
    content = requests.get(target,headers = headers)
    html = bs(content.text)
    div = html.find_all("div",class_="listmain")
    #print(type(all_title)) #a result set
    titles = bs(str(div[0]))
    a = titles.find_all('a')
    chapter_names = []
    chapter_urls = []
    for title in a:
        #print(title.string,title.get("herf"))
        chapter_name = title.string
        chapter_url = target + title.get('href')
        chapter_names.append(chapter_name)
        chapter_urls.append(chapter_url)
        print(chapter_name, chapter_url)
    
def get_content(chapter_name, chapter_url):
    pass

if __name__ == "__main__":
    target = "http://www.bilibili.com"
    get_urls(target)
import requests
from bs4 import BeautifulSoup as bs    
