<!-- Back to top link-->
<a name="readme-top"></a>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]


<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/ELLISB1000/Refresh-ADPassword">
    <img src="Public/logo.png" alt="Logo" width="400" height="400">
  </a>

<h3 align="center">Refresh-ADPassword</h3>

  <p align="center">
    A simple script to refresh an expired Active Directory password.
    <br />
    <a href="https://github.com/ELLISB1000/Refresh-ADPassword/issues">Report Bug</a>
    ·
    <a href="https://github.com/ELLISB1000/Refresh-ADPassword/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

A very useful script to refresh an expired password for a user account in Active Driectory. This is done by setting the AD attribute `pwdlastset` to todays date. To do this you set the `pwdlastset` field to `0`, this means that the password has never been set. Once that is applied you go back and set the attribute to `-1`, this sets the password to the current date and time. The password will then no longer flag as expired and the user can continue to use the current password.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- GETTING STARTED -->
## Getting Started

To get a local copy up and running follow these simple example steps.


### Prerequisites

You will need have the ActiveDirectory PowerShell module installed, if you are running Windows 10 version 1809 and later run the following command.

* powershell
  ```powershell
  Add-WindowsCapability -Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0 -Online
  ```

If you are running Windows Server 2008 to 2022 run the following command.

* powershell
  ```powershell
  Install-WindowsFeature -Name "RSAT-AD-PowerShell" -IncludeAllSubFeature
  ```

If you are running a Windows 10 version 1809 prior to 1809 you can install the RSAT tools from [here](https://www.microsoft.com/en-us/download/details.aspx?id=45520)


### Installation

1. Browse to the folder you store your scripts `e.g. cd C:\Script`
2. Clone the repo
   ```powershell
   Invoke-WebRequest -Uri https://raw.githubusercontent.com/ELLISB1000/Refresh-ADPassword/main/Refresh-ADPassword.ps1 -OutFile .\Refresh-ADPassword.ps1
   ```

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- USAGE EXAMPLES -->
## Usage

Run the script against a single user account.

   ```powershell
   .\Refresh-ADPassword.ps1 -username "Test.User"
   ```

Run the script against multiple user accounts from the output of Get-ADuser.

   ```powershell
   $ADUsers = Get-ADUser -filter {enabled -eq $true} #You can customize the filter applied
   foreach ($ADUser in $ADUsers) {.\Refresh-ADPassword.ps1 -username $ADUser.samaccountname}
   ``` 

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- ROADMAP -->
## Roadmap

- [ ] Ability to run script against users in a csv file.
- [ ] Add logging

See the [open issues](https://github.com/ELLISB1000/Refresh-ADPassword/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- LICENSE -->
## License

Distributed under the MIT License. See `LICENSE` for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

[Ellis Barrett](https://ellisbarrett.com)

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/ELLISB1000/Refresh-ADPassword.svg?style=for-the-badge
[contributors-url]: https://github.com/ELLISB1000/Refresh-ADPassword/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/ELLISB1000/Refresh-ADPassword.svg?style=for-the-badge
[forks-url]: https://github.com/ELLISB1000/Refresh-ADPassword/network/members
[stars-shield]: https://img.shields.io/github/stars/ELLISB1000/Refresh-ADPassword.svg?style=for-the-badge
[stars-url]: https://github.com/ELLISB1000/Refresh-ADPassword/stargazers
[issues-shield]: https://img.shields.io/github/issues/ELLISB1000/Refresh-ADPassword.svg?style=for-the-badge
[issues-url]: https://github.com/ELLISB1000/Refresh-ADPassword/issues
[license-shield]: https://img.shields.io/github/license/ELLISB1000/Refresh-ADPassword.svg?style=for-the-badge
[license-url]: https://github.com/ELLISB1000/Refresh-ADPassword/blob/master/LICENSE
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/ellis-barrett
