Дополнительно:

* Selenium & WebDriver: [ссылка](https://selenium-python.readthedocs.io/)
* [SelectorGadget](https://chrome.google.com/webstore/detail/selectorgadget/mhjhnkcfbdhnjickkkdbjoemdmbfginb)
*  [Отправка писем](https://nbviewer.jupyter.org/github/allatambov/PyProg-2018/blob/master/14-12/py-gmail.ipynb) gmail

* http://math-info.hse.ru/f/2018-19/py-polit/vk-auth.pdf
```
br = wd.Chrome('/Users/allat/Downloads/chromedriver') 

def get_address(reg, uik):
    
    br.get("http://www.cikrf.ru/services/lk_address/?do=find_by_uik")
    uik_field = br.find_element_by_css_selector('#uik')
    uik_field.send_keys(str(uik))
    reg_field = br.find_element_by_name('subject')
    reg_field.send_keys(reg)

    button = br.find_element_by_link_text("Отправить запрос")
    button.click() 

    soup = BeautifulSoup(br.page_source, 'lxml')

    texts = [i.text for i in soup.find_all('p')]
    addr = list(filter(lambda x: 'Адрес помещения для голосования'in x, 
                texts))[0]
    return addr
    ```
