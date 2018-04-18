import urllib.request
import urllib.parse
import os
import time

def open_url(url):
    req = urllib.request.Request(url)
    req.add_header('User-Agent', 'Mozilla/5.0 (Windows NT 6.1; WOW64; rv:52.0) Gecko/20100101 Firefox/52.0')
    respond = urllib.request.urlopen(req)
    html = respond.read()
    return html

def  get_title(url):
    html = open_url(url).decode('utf-8')    
    a = html.find('f16 video-title')
    title_list = []
    while a != -1:
        b = html.find(r'</h2>', a, a+255)
        if b != -1:
            src =html[a+17:b]
            title_list.append(src)
        else:
            b = a + 17
        a = html.find('f16 video-title',b)
    return title_list
def  get_urls(url):
    html = open_url(url).decode('utf-8')
    a = html.find(r'/index.php')
    url_list = []
    while a != -1:
        b = html.find(r'a=show&catid', a, a+255)
        if b != -1:
            src =html[a:b+23]
            src = 'http://www.caobi002.com'+src
            url_list.append(src)
        else:
            b = a + 23
        a = html.find(r'/index.php',b)
    return url_list
def  get_agree(url):
    html = open_url(url).decode('utf-8')
    a = html.find('f-l icons ico-praise')
    agree_list=[]
    while a != -1:
        b = html.find(r'/span', a, a+255)
        if b != -1:
            src =html[a+22:b-1]
            agree_list.append(int(src))
        else:
            b = a + 16
        a = html.find('f-l icons ico-praise',b)

    return agree_list


def save_img(field,img_addes):
    for each in img_addes:
        fileName = each.split('/')[-1]
        with open(fileName,'wb') as f:
            imgs = open_url(each)
            f.write(imgs)

def get_img_list_url(url):
    list_list=[]
    html = open_url(url).decode('gbk')
    a = html.find('/yijingtupian/')
    while a != -1:
        b = html.find('.html', a, a+255)
        if b != -1:
            src = html[a+13:b+5]
            print(src)
        else:
            b = a + 15
    a = html.find('/yijingtupian/')

def down(field= 'MYdownlode',pages =10):
    try:
        os.mkdir(field)
    except:
        print("文件夹已经存在！")
    os.chdir(field)
    url = 'http://www.qqjay.com/yijingtupian/173355.html'
    url2= 'http://www.qqjay.com/yijingtupian/list_72_1.html'
    img_addrs = get_imgurl(url)
    get_img_list_url(url2)
   # save_img(field, img_addrs)
if __name__ == '__main__':
    dicts ={}

    for i in range(1,50):
        urllist = 'http://www.caobi002.com/list-9-'+ str(i) +'.html'

        agrees =get_agree(urllist)
        titles = get_title(urllist)
        url = get_urls(urllist)
        dict1 = dict(zip(titles,url))
        dictionary = dict(zip(dict1.items(),agrees))
        dicts.update(dictionary)
    time.sleep(3)
    for i in range(50,150):
        urllist = 'http://www.caobi002.com/list-9-'+ str(i) +'.html'

        agrees =get_agree(urllist)
        titles = get_title(urllist)
        url = get_urls(urllist)
        dict1 = dict(zip(titles,url))
        dictionary = dict(zip(dict1.items(),agrees))
        dicts.update(dictionary)
    time.sleep(3)
    for i in range(150, 250):
        urllist = 'http://www.caobi002.com/list-9-' + str(i) + '.html'

        agrees = get_agree(urllist)
        titles = get_title(urllist)
        url = get_urls(urllist)
        dict1 = dict(zip(titles, url))
        dictionary = dict(zip(dict1.items(), agrees))
        dicts.update(dictionary)
    time.sleep(3)
    for i in range(250, 320):
        urllist = 'http://www.caobi002.com/list-9-' + str(i) + '.html'

        agrees = get_agree(urllist)
        titles = get_title(urllist)
        url = get_urls(urllist)
        dict1 = dict(zip(titles, url))
        dictionary = dict(zip(dict1.items(), agrees))
        dicts.update(dictionary)
    dicts = sorted(dicts.items(),key = lambda x:x[1],reverse = True)
    str_dict = '\n'.join(str(i) for i in dicts)
    print (len(dicts))
    with open('results.txt','w',encoding='utf-8') as fd:
        fd.write(str_dict)

