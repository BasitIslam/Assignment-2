
from selenium import webdriver
from selenium.webdriver.chrome.service import Service
from webdriver_manager.chrome import ChromeDriverManager
from selenium.webdriver.common.by import By
import time


class Lesco_bills():

    def __init__(self):
        self.counter = 0

    def bill_downloader(self):
        
        for i in range (9300000,9300010):
            
            #this is the path to driver program
            driver = webdriver.Chrome(executable_path=r"E:\chromedriver.exe") 
            #link to where we have to fetch data
            driver.get("http://www.lesco.gov.pk/Modules/CustomerBill/CheckBill.asp")
            #filling the form
            driver.find_element(By.NAME, 'txtCustID').send_keys(i)
            #looking for submission buttons
            driver.find_element(By.NAME, 'form2').submit()
            driver.find_element(By.LINK_TEXT, "Consumption & Payment History").click()
            self.counter +=1
            print("History for Bill Number %s is sucessfully checked."%(self.counter))
            time.sleep(4)
            driver.quit()

if __name__ == "__main__":
        
    bills = Lesco_bills()
    bills.bill_downloader()
