# Understanding the Six PowerShell Profiles

**Summary:** Microsoft Scripting Guy, Ed Wilson, discusses the six
different Windows PowerShell profiles, and when to use each.

## Q:
Hey, Scripting Guy! Dude, I have been reading some of the posts in your
most excellent blog; and first of all, I want to say I think you are
great. Now for the question: I do not get the Windows PowerShell
profile. I mean I get it, but not really. Here is part of my problem. I
put some things in the profile, and then I go back and they are not
there. Like, what is up with that? I hope you can help me. By the way, I
am, like, totally looking forward to seeing you and the Scripting Wife
at TechEd 2012 in Orlando. You will know me, because I sort of look like
Urkel, and I always wear plaid shirts (but I don’t wear suspenders).

—BB

## A:
Hello BB,

Microsoft Scripting Guy, Ed Wilson, is here. Last week was an absolutely
great week. The Scripting Wife and I had dinner one night with Rich from
the NYC Windows PowerShell Users Group (he is also a moderator for the
Scripting Guys forum and writer of a couple of guest blogs). Rich was
kind enough to bring me some Gunpower green tea, and I am sipping some
right now. It is wonderful with a half teaspoon of organic lavender
added to the pot. We also had the PowerScripting Podcast with the two
winners of the 2012 Scripting Games and Jeffrey Snover. That
conversation was fun and informative. I also enjoy talking to Jeffrey,
and I look forward to sitting-in on at least one of his sessions at
Microsoft TechEd 2012.

## Six, count ‘em, six different PowerShell profiles

BB, there is no doubt that you are a bit confused with Windows
PowerShell profiles. There are, in fact, six different profiles. The
Windows PowerShell console and the Windows PowerShell ISE have their own
profiles. In addition, there are profiles for the current user and
profiles for all users. The table that follows lists the six profiles
and their associated locations.

| Description                          | Path                                                                          |
| ------------------------------------ | ----------------------------------------------------------------------------- |
| Current User, Current Host - Console | `$Home\[My ]Documents\WindowsPowerShell\Profile.ps1`                          |
| Current User, All Hosts              | `$Home\[My ]Documents\Profile.ps1`                                            |
| All Users, Current Host - Console    | `$PsHome\Microsoft.PowerShell_profile.ps1`                                    |
| All Users, All Hosts                 | `$PsHome\Profile.ps1`                                                         |
| Current User, Current Host - ISE     | `$Home\[My ]Documents\WindowsPowerShell\Microsoft.P owerShellISE_profile.ps1` |
| All Users, Current Host - ISE        | `$PsHome\Microsoft.PowerShellISE_profile.ps1`                                 |

### Understanding the six Windows PowerShell profiles

The first thing to do to understand the six Windows PowerShell profiles
is to keep in mind that they move. They change (sort of like the
staircases at [Hogwarts](http://en.wikipedia.org/wiki/Hogwarts)). As
long as you realize that they are a moving target, you will be fine. In
most cases, when talking about the Windows PowerShell profile, people
are referring to the **Current User, Current Host** profile. In fact, if
no one qualifies the Windows PowerShell profile with its associated
scope or description, it is safe to assume that they are talking about
the **Current User, Current Host** profile.

**Note:** A Windows PowerShell profile (any one of the six) is simply a
Windows PowerShell script. It has a special name, and it resides in a
special place, but it is simply a script. In this regard, it is sort of
like the old-fashioned [autoexec.bat](http://en.wikipedia.org/wiki/AUTOEXEC.BAT)
batch file. Because the Windows PowerShell profile is a Windows
PowerShell script, you must enable the Script Execution policy prior to
configuring and using a Windows PowerShell profile. For information
about the Script Execution policy refer to ~~this collection of Hey,
Scripting Guy! Blogs~~.

### Examining the `$profile` variable

When you query the `$profile` automatic variable, it returns the path to
the **Current User, Current Host** profile. This makes sense, and it is
a great way to easily access the path to the profile. The following
script illustrates this technique from within the Windows PowerShell
console.

```powershell
PS C:\> $PROFILE
C:\Users\User\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

Inside the Windows PowerShell ISE, when I query the `$profile` automatic
variable, I receive the output that is shown here.

```powershell
PS C:\Users\User> $PROFILE
C:\Users\User\Documents\WindowsPowerShell\Microsoft.PowerShellISE_profile.ps1
```

To save you a bit of analyzing...

The difference between the Windows PowerShell console **Current User,
Current Host** profile path and the Windows PowerShell ISE **Current
User, Current Host** profile path is three letters: **ISE**.

BB, these three letters are probably causing you problems. More than
likely, you are setting something in your Windows PowerShell console
profile, and it is not available inside the Windows PowerShell ISE.

**Unraveling the profiles**

You can pipe the `$profile` variable to the `Get-Member` cmdlet and see
additional properties that exist on the `$profile` variable. This
technique is shown here.

```powershell
PS C:\> $PROFILE | Get-Member -MemberType NoteProperty | select Name

Name
----
AllUsersAllHosts
AllUsersCurrentHost
CurrentUserAllHosts
CurrentUserCurrentHost
```

If you are accessing the `$profile` variable from within the Windows
PowerShell console, the `AllUsersCurrentHost` and the 
`CurrentUserCurrentHost` note properties refer to the Windows PowerShell
console. If you access the `$profile` variable from within the Windows
PowerShell ISE, the `AllUsersCurrentHost` and the
`CurrentUserCurrentHost` note properties refer to the Windows PowerShell
ISE profiles.

**Using the $profile variable to refer to more than the current host**

When you reference the `$profile` variable, by default it refers to the
**Current User, Current Host** profile. If you pipe the variable to the
`Format-List` cmdlet, it still refers to the **Current User, Current
Host** profile. This technique is shown here.

```powershell
PS C:\> $PROFILE | Format-List *
C:\Users\User\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
```

This leads to a bit of confusion, especially because the `Get-Member`
cmdlet reveals the existence of multiple profiles and multiple note
properties. The way to see all of the profiles for the current host, is
to use the force parameter. It reveals the hidden properties. The
command illustrating this technique is shown here.

The command and the associated output from the command are shown in the
image that follows.

```powershell
PS C:\> $PROFILE | Format-List * -Force

AllUsersAllHosts       : C:\Windows\System32\WindowsPowerShell\v1.0\profile.ps1
AllUsersCurrentHost    : C:\Windows\System32\WindowsPowerShell\v1.0\Microsoft.PowerShell_profile.ps1
CurrentUserAllHosts    : C:\Users\User\Documents\WindowsPowerShell\profile.ps1
CurrentUserCurrentHost : C:\Users\User\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
Length                 : 80

PS C:\>
```

It is possible to directly access each of these specific properties just
like you would access any other property-via dotted notation. This
technique is shown here.

```powershell
$PROFILE.CurrentUserAllHosts
```

The path to each of the four profiles for the Windows PowerShell console
are shown in the image that follows.

```powershell
PS C:\> $PROFILE.CurrentUserAllHosts
C:\Users\User\Documents\WindowsPowerShell\profile.ps1
PS C:\> $PROFILE.CurrentUserCurrentHost
C:\Users\User\Documents\WindowsPowerShell\Microsoft.PowerShell_profile.ps1
PS C:\> $PROFILE.AllUsersAllHosts
C:\Windows\System32\WindowsPowerShell\v1.0\profile.ps1
PS C:\> $PROFILE.AllUsersCurrentHost
C:\Windows\System32\WindowsPowerShell\v1.0\Microsoft.PowerShell_profile.ps1
PS C:\>
```

### Determine if a specific profile exists

To determine if a specific profile exists, use the `Test-Path` cmdlet
and the appropriate flavor of the `$profile` variable. For example, to
determine if a **Current User, Current Host** profile exists you can use
the `$profile` variable with no modifier, or you can use the
`CurrentUserCurrentHost` note property. The following example
illustrates both of these.

```powershell
PS C:\> Test-Path $PROFILE
True
PS C:\> Test-Path $PROFILE.CurrentUserCurrentHost
True
PS C:\>
```

In the same manner, the other three profiles that apply to the current
host (in this example, I am using the Windows PowerShell console) are
determined to not exist. This is shown in the code that follows.

```powershell
PS C:\> Test-Path $PROFILE.AllUsersAllHosts
False
PS C:\> Test-Path $PROFILE.AllUsersCurrentHost
False
PS C:\> Test-Path $PROFILE.CurrentUserAllHosts
False
PS C:\>
```

### Creating a new profile

To create a new profile for current user all hosts, use the
`CurrentUserAllHosts` property of the `$profile` automatic variable, and
the `New-Item` cmdlet. This technique is shown here.

```powershell
PS C:\> New-Item $PROFILE.CurrentUserAllHosts -ItemType File -Force
    Directory: C:\Users\User\Documents\WindowsPowerShell

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---         5/17/2012   2:59 PM          0 profile.ps1
```

To open the profile for editing, use the `ise` alias as shown here.

```powershell
ise $PROFILE.CurrentUserAllHosts
```

When you are finished editing the profile, save it, close the Windows
PowerShell console, reopen the Windows PowerShell console, and test that
your changes work properly.

BB, that is all there is to using the `$profile` variable to discover
different Windows PowerShell profiles. Windows PowerShell Profile Week
will continue tomorrow when I will talk about editing and testing a
Windows PowerShell profile.

I invite you to follow me on [Twitter](http://bit.ly/scriptingguystwitter)
and [Facebook](http://bit.ly/scriptingguysfacebook). If you have any
questions, send email to me at [scripter@microsoft.com](scripter@microsoft.com),
or post your questions on the [Official Scripting Guys Forum](http://bit.ly/scriptingforum).
See you tomorrow. Until then, peace.

## Reference

* [Understanding the Six PowerShell Profiles (Microsoft)](https://devblogs.microsoft.com/scripting/understanding-the-six-powershell-profiles/)
* [Understanding the Six PowerShell Profiles (Internet Archive)](https://web.archive.org/web/20121105003839/http://blogs.technet.com/b/heyscriptingguy/archive/2012/05/21/understanding-the-six-powershell-profiles.aspx)
* [Scripting Blog](https://devblogs.microsoft.com/scripting/)