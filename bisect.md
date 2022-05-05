# GIT BISECT

Bisect allowes you to find the specific commit that introduced a bug in a convenient way.

You will have good and bad commits, either with the bug or without.

We chackout to the latest - most recent - commit, where there is the bug and we run:

```bash
git bisect start
```

now we will tell git that in this commit there is the bug

```bash
git bisect bad
```

now, through git log, we find a commit were we know there is no issue

```bash
git log
```

here we pick a old commit without the bug and we mark it as good

```bash
git bisect good d255f8a8e5ea6dbaac078fc7f094243294360a78
```

this will check us out to a branch in the middle, and we need to tell git if it's good or bad 

```bash
git bisect bad
```

so he will continue getting closer to the initial good commit and requiring us to judge it

```bash
git bisect good
```

when there are no commits in between good and bad, we know what commit introduced the bug. (output: 8162b7f5b590f2211916e05305c762e736f76aa3)

```bash
git bisect reset
```

we can show the commit changes by running:

```bash
git show 8162b7f5b590f2211916e05305c762e736f76aa3
```

we can now revert the commit with:

```bash
git revert 8162b7f5b590f2211916e05305c762e736f76aa3
```