Before you can use selenium to control chrome browser in Linux (wsl);

Install Chrome browser for linux by;
    Chrome browser is not available by default in the linux repository so we have to download the .deb file
    run
    wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

    sudo dpkg -i google-chrome-stable_current_amd64.deb  # this install chrome browser from the .deb file
    
    sudo apt --fix-broken install # to install the dependencies chrome browser needs to run

STEP 2
Check your chrome version;
     google-chrome-stable --version

STEP 3
Next we need to install chromedriver which allows us to use selenium to control chrome.
The chromedriver should be for your chrome version

a) since we installed the latest chrome , let us check for the compactible chrome driver

chrome_driver=$(curl "https://chromedriver.storage.googleapis.com/LATEST_RELEASE") && \
echo "$chrome_driver"

b) download the chrome driver

curl -Lo chromedriver_linux64.zip "https://chromedriver.storage.googleapis.com/\
${chrome_driver}/chromedriver_linux64.zip"          # this saves the download to chromedriver_linux64.zip

c) d) Unzip the binary file and make it executable

mkdir -p "chromedriver/stable" && \
unzip -q "chromedriver_linux64.zip" -d "chromedriver/stable" && \
chmod +x "chromedriver/stable/chromedriver"

