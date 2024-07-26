from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.support import expected_conditions as EC

# Initialize WebDriver (Here, we use Chrome; you can use any other WebDriver)
driver_path = '/path/to/chromedriver'  # Update this to the path of your ChromeDriver
driver = webdriver.Chrome(executable_path=driver_path)

try:
    # Open the URL
    driver.get('https://www.imdb.com/search/name/')

    # Wait for the first name input to be present and send keys
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, 'name'))
    ).send_keys('Leonardo')

    # Wait for the birth place input to be present and send keys
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, 'birth_place'))
    ).send_keys('Los Angeles')

    # Wait for the birthday month drop-down to be present and select
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, 'birth_monthday'))
    ).send_keys('November')

    # Wait for the birthday year drop-down to be present and select
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, 'birth_year'))
    ).send_keys('1974')

    # Wait for the gender drop-down to be present and select
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.ID, 'gender'))
    ).send_keys('Male')

    # Wait for the search button to be present and click
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.XPATH, '//button[@type="submit"]'))
    ).click()

    # ... (additional actions if needed)

finally:
    # Close the browser after a short wait (for observation if running interactively)
    WebDriverWait(driver, 10).until(
        EC.presence_of_element_located((By.CLASS_NAME, 'lister-item'))
    )
    driver.quit()
