# week-one
Learn about git

[00:00:00]
>> Nina: Let's talk about the three areas in Git where code lives. The first is the working area, sometimes also called the working tree. The second is the staging area, you might also see this called the cache or the index and the last is the repository.
>> Nina: The working area, in brief, is the files that are not in the staging area.

[00:00:29] They're not handled by Git. They're kind of just in your local directory. They can also be called untracked files. The working area is like your scratch space, it's where you can add new content, you can modify delete content, if the content that you modify or delete is in your repository you don't have to worry about losing your work.

[00:00:53] The staging area, that's what files are going to be a part of your next commit. It's how Git knows what is going to change between the current commit and the next one. We're gonna deep-dive into the staging area in the next section. Briefly, the repository, that's the files that Git actually knows about.

[00:01:18] The repository contains all of your commits. And the commit is a snapshot of what your working and staging area look like at the time of the commit. It's in your .git directory. And that's all of the files in your repository, they're stored away safely, you can continue to make changes as you work and you can always check out a fresh copy if you need one.

[00:01:50] Let's take a closer look at the staging area.
>> Nina: So very, very important, the staging area. That's how Git knows what's gonna change between your current commit and your next commit.
>> Nina: A clean staging area, people think it's empty, but that's not really the case. A clean staging area isn't empty.

[00:02:21] Actually, what's going on is the baseline staging area is a copy of your latest commit. So it contains a list of files that were in your last commit, as well as the SHA1 hash of those files as they were in their last commit. The way that Git stores this information, the index is actually a binary file in the .git directory.

[00:02:51] Don't try to open it you'll just, get a bunch of yucky data. But I'll show you how to peek in that in just a few minutes. We're gonna do that using another plumbing command.
>> Nina: When you add, remove, rename files to the staging area, Git knows because the SHA1 of the changed file is now different from the SHA1 of the file that was in the repository.

[00:03:27]
>> Nina: In order to look at our index, We use the plumbing command git ls-files with the -s flag.
>> Nina: So the first few numbers are the mode, then the SHA matching the SHA in the repository, followed by the file name.
>> Nina: To move files in and out of the staging area, you should all be pretty familiar with these commands if you've been using Git.

[00:04:08] If you want to add a file to the next commit, git add, file name. If you want to delete a file in the next commit, git rm. A lot of people, in their workflows, tend to remove the file from their working area, and then they have to stage it in a separate step, and it's kind of annoying.

[00:04:29] So you can just tell Git to remove the file directly, and it'll do that in one step, git rm. If you wanna rename a file, that's going to be part of your next commit, you can just use the git mv command, mv for move.
>> Nina: Now git add-p, have any of you in class used this command?

[00:04:54] No? It's really just one of my absolute favorite tools. It allows you to stage your commit in chunks interactively. It's especially useful if you've done too much work for one commit, you wanna break it up, you don't know how. Sometimes people wonder why Git needs a staging area at all.

[00:05:20] Wouldn't it be simply if you could just commit everything in your working area in one go? And you can, but it's not a recommended workflow, that's git commit -a. But git add -p is kind of a shining highlight of how useful the staging area can be. You can have a bunch of changes in your working directory and then pick and choose which of those changes should be in the next commit.

[00:05:48] So here is an example of git add-p I kinda have ...diff displayed it'll show you the diff between your staging area, and your commit, your repository version. So even if you use this tool a lot, you don't have to remember any of these commands. It will ask you, do you want to stage this hunk?

[00:06:15] Y, N, Q, A, D. What does all of that even mean? The only command you need to remember is the question mark. When you hit question mark at this stage, it'll print a complete description of all the commands. If you wanna exit a partial staging, you can just press Q.

[00:06:36] A friend of mine loves using this feature when he's staging work while he's debugging. So he'll use git add-p to add the changes but skip over the debugging statements while he's committing. And he'll just leave those in place as he works. So git add-p, question mark. That's the two commands you need to remember.

[00:07:08]
>> Nina: When you unstage files from the staging area, remember you're not removing the files. The staging area isn't empty. What you're doing is you're just replacing them with a copy that's currently in a repository.
>> Nina: So a little bit of how content moves in Git. We can use that git connect-a to move straight from the working area to the repository.

[00:07:35] We add files from the working area to the staging area, we commit from the staging area to the repository. And we check out from from the repository to the staging area and the working area.
