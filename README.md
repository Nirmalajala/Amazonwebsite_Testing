package tets;

import java.nio.channels.AlreadyBoundException;
import java.util.Iterator;
import java.util.List;
import java.util.Set;
import java.util.concurrent.TimeUnit;

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.openqa.selenium.support.ui.Select;

public class Practice {

	public static void main(String[] args) {
		System.setProperty("webdriver.chrome.driver", "C:\\Testing\\tets\\src\\main\\resources\\drivers\\chromedriver-win64\\chromedriver.exe");  
        WebDriver driver = new ChromeDriver();
        driver.manage().window().maximize();
        driver.get("https://www.amazon.in");
        
        
        
       WebElement sigin = driver.findElement(By.xpath("//span[@class='nav-line-2 ']"));
       if (sigin.isDisplayed()) {
           System.out.println("Sign In button is visible.");
       } else {
           System.out.println("Sign In button is not visible.");
       }
       
        driver.findElement(By.xpath("//span[@class='nav-line-2 ']")).click();        		
 		

     WebElement userEmail =  driver.findElement(By.id("ap_email"));
     userEmail.sendKeys("8179758728");
     driver.findElement(By.id("continue")).click();

    WebElement userPassword =  driver.findElement(By.id("ap_password"));
    userPassword.sendKeys("Nirmala@123456");
     driver.findElement(By.id("signInSubmit")).click();
        
     
     
     
       WebElement searchbox =  driver.findElement(By.id("twotabsearchtextbox")); 
       searchbox.sendKeys("dairy milk chocolates");
       if (searchbox.isDisplayed()) {
           System.out.println("Search box is displayed. Proceeding with search.");
       } else {
           System.out.println("Page item will fail to navigate to the page: Search box not displayed.");
       }        
       driver.findElement(By.id("nav-search-submit-button")).click();

       
       
      driver.findElement(By.linkText("Cadbury Dairy Milk Crackle Chocolate Bar, 36 Grams (Pack of 10)")); 
      if (driver.findElement(By.linkText("Cadbury Dairy Milk Crackle Chocolate Bar, 36 Grams (Pack of 10)")).isDisplayed()) {
          System.out.println("Product link is visible.");

          driver.findElement(By.linkText("Cadbury Dairy Milk Crackle Chocolate Bar, 36 Grams (Pack of 10)")).click();
          System.out.println("Product link clicked successfully.");
      } else {
          System.out.println("Product link is not visible on the page.");
      }
        
        Set<String> handles = driver.getWindowHandles();
        Iterator wins = handles.iterator();
        String parentid = (String) wins.next();
        String childid = (String) wins.next();
        System.out.println(parentid);
        System.out.println(childid);
        driver.switchTo().window(childid);
        
        
        Select sc = new Select(driver.findElement(By.cssSelector("#quantity")));
        sc.selectByIndex(3);
        List<WebElement> alloptions = sc.getOptions();
        
        
        for(WebElement eachOption:alloptions)
     	   System.out.println( eachOption.getText());

        if (driver.findElement(By.cssSelector("#quantity")).isDisplayed()) {
            System.out.println("Quantity 3 is available in the dropdown.");
        } else {
            System.out.println("Quantity 3 is not available in the dropdown.");
        }
        
        
       driver.findElement(By.xpath("//input[@id='add-to-cart-button']")).click();
       driver.findElement(By.name("proceedToRetailCheckout")).click();
       
       
	}
        

		}
	



