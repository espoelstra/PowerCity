# PowerCity v0.0.1 - Based on TeamCityPowerShell by endjin et al.

## About

PowerCity aims to take the work of endjin on TeamCityPowerShell and enable you to do more than just Get-* from a TeamCity instance.

## Usage
### Sample
<pre>
$parameters = @{ 
	 ConnectionDetails = @{
		 ServerUrl = "teamcity.codebetter.com"
		 Credential = New-Object System.Management.Automation.PSCredential("teamcitysharpuser", (ConvertTo-SecureString "qwerty" -asplaintext -force))
		 UseSsl = $false
		 IsGuest = $false 
	 }
	 BuildConfigId = "bt437"
}

$builds = Get-BuildConfigsByBuildConfigId @parameters

foreach($build in $builds)
{
	Write-Host $build.Number
}
</pre>

The following cmdlets are supported:

<pre>
 o Get-AllAgents
 o Get-AllBuildConfigs
 o Get-ArtifactsByBuildId
 o Get-Artifact
 o Get-ArtifactsAsArchive *
 o Get-BuildConfigByConfigurationName
 o Get-AllBuildsOfStatusSinceDate
 o Get-AllBuildsSinceDate
 o Get-AllChanges
 o Get-AllGroupsByUserName
 o Get-AllProjects
 o Get-AllRolesByUserName *
 o Get-AllServerPlugins *
 o Get-AllUserGroups
 o Get-AllUserRolesByUserGroup
 o Get-AllUsers *
 o Get-AllUsersByUserGroup
 o Get-AllVcsRoots
 o Get-BuildConfigByConfigurationId
 o Get-BuildConfigByConfigurationName
 o Get-BuildConfigByProjectIdAndConfigurationId
 o Get-BuildConfigByProjectIdAndConfigurationName
 o Get-BuildConfigByProjectNameAndConfigurationId
 o Get-BuildConfigByProjectNameAndConfigurationName
 o Get-BuildConfigsByBuildConfigId
 o Get-BuildConfigsByConfigIdAndTag
 o Get-BuildConfigsByConfigIdAndTags
 o Get-BuildConfigsByProjectId
 o Get-BuildConfigsByProjectName
 o Get-BuildsByBuildLocator *
 o Get-BuildsByUserName
 o Get-ChangeDetailsByBuildConfigId
 o Get-ChangeDetailsByChangeId
 o Get-ErrorBuildsByBuildConfigId *
 o Get-FailedBuildsByBuildConfigId *
 o Get-LastBuildByAgent
 o Get-LastBuildByBuildConfigId
 o Get-LastChangeDetailByBuildConfigId
 o Get-LastErrorBuildByBuildConfigId *
 o Get-LastFailedBuildByBuildConfigId
 o Get-LastSuccessfulBuildByBuildConfigId
 o Get-LatestArtifact
 o Get-NonSuccessfulBuildsForUser
 o Get-ProjectById
 o Get-ProjectByName
 o Get-ServerInfo
 o Get-SuccessfulBuildsByBuildConfigId
 o Get-VcsRootById
 o New-TeamCityUrl
 o New-TeamCityWebClientConnection
</pre>
\* the function has a ignored specification pending investigation  
To discover what parameters are required for each cmdlet use the Get-Help cmdlet i.e.:
 
	Get-Help Get-BuildConfigsByBuildConfigId

which will return

	Get-BuildConfigsByBuildConfigId [[-ConnectionDetails] <Hashtable>] [[-BuildConfigId] <String>]

The ConnectionDetails hashtable requires the following values

	ConnectionDetails = @{
		ServerUrl = "teamcity.codebetter.com"
		Credential = New-Object System.Management.Automation.PSCredential("teamcitysharpuser", (ConvertTo-SecureString "qwerty" -asplaintext -force))
		UseSsl = $false
		IsGuest = $false 
	}

At a minimum the following values are required:

	ConnectionDetails = @{
		ServerUrl = "teamcity.codebetter.com"
		Credential = New-Object System.Management.Automation.PSCredential("teamcitysharpuser", (ConvertTo-SecureString "qwerty" -asplaintext -force))
	}

If you don't want to embedd TeamCity credentials you can enter them interactively using:

	$parameters = @{ 
		ConnectionDetails = @{
			ServerUrl = "teamcity.codebetter.com"
			Credential = Get-Credential
		}
		BuildConfigId = "bt437"
	}

Alternatively you can retrieve them from disk using this PowerShell Cookbook recipie: http://www.leeholmes.com/blog/2008/06/04/importing-and-exporting-credentials-in-powershell/

For full documentation on how to use each Cmdlet see the Pester Specifications contained within TeamCity.Tests.ps1 and TeamCity-Artifacts.Tests.ps1

To run the full suite of BDD specs invoke "run-specs.bat" in the root of this project.
 
 
## Ingredients
PowerCity makes use of the following tools and frameworks:

* [TeamCitySharp](https://github.com/stack72/TeamCitySharp)
* [Pester](https://github.com/scottmuc/Pester)


## Install
When there's something to release, it'll be found on the PSGallery. Instructions to install from source to come.


## Contribute
Contribution guidelines TBD.

## Support / Help
Follow [@Drizzt396](http://twitter.com/drizzt396) on twitter.

Report bugs & issues on [the tracker](https://github.com/requiemforatheory/PowerCity/issues).

## Credits & Thanks
Howard van Rooijen, James Dawson & Contributors for TeamCityPowerShell
Paul Stack & Contributors for TeamCitySharp

## Version History
2017.01.24 - v0.0.1 - First forked from TeamCityPowerShell