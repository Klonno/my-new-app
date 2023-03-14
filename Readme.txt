React App in Visual Studio


Prerequisites:

Install Linux on Windows with WSL
https://learn.microsoft.com/en-us/windows/wsl/install
Powershell commands
wsl --list
wsl --list --online
wsl --install -d Ubuntu-22.04
https://learn.microsoft.com/en-us/windows/wsl/basic-commands
wsl --distribution Ubuntu-22.04 --user scott



/home is the equivilent of c:/users. A place to put my files (my documents, downloads etc)

scott@A37573-M:~$ npx create-react-app my-app
Command 'npx' not found, but can be installed with:
sudo apt install npm

From https://learn.microsoft.com/en-us/visualstudio/javascript/tutorial-create-react-app?view=vs-2022 :

Prerequisites
Make sure to install the following:

Visual Studio 2022 or later. Go to the Visual Studio downloads page to install it for free.
npm (https://www.npmjs.com/), which is included with Node.js
npx (https://www.npmjs.com/package/npx)

https://nodejs.org/en/download/

In powershell:
npm config set registry http://registry.npmjs.org/

No SPA development server running at error:
npm install --save-dev run-script-os

dotnet new react -o my-new-app
cd my-new-app

if app wont start
npm install
if Error: SSL Error: SELF_SIGNED_CERT_IN_CHAIN -
npm config set strict-ssl false

Each page is a javascript page in ./components

In fetchData.js

async populateWeatherData() {
    const response = await fetch('weatherforecast');
    const data = await response.json();
    this.setState({ forecasts: data, loading: false });
	
Calls ForecastCOntroller.cs
    [HttpGet]
    public IEnumerable<WeatherForecast> Get()
    {
        return Enumerable.Range(1, 5).Select(index => new WeatherForecast
        {
            Date = DateOnly.FromDateTime(DateTime.Now.AddDays(index)),
            TemperatureC = Random.Shared.Next(-20, 55),
            Summary = Summaries[Random.Shared.Next(Summaries.Length)]
        })
        .ToArray();
    }	
  }
