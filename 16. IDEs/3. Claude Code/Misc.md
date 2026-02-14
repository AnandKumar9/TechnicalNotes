[toc]

##### AgentSDK and CLI access

There are [Python](https://platform.claude.com/docs/en/agent-sdk/python) and [TS](https://platform.claude.com/docs/en/agent-sdk/typescript) packages that can let you communicate with Claude Code and let it do things. 

([Documentation](https://code.claude.com/docs/en/headless))

![image-20260216141019359](./assets/image-20260216141019359.png)

There is also CLI access for scripts and CICD, which is nothing but **claude -p** which basically lets you run any claude command non-interactively. 

![image-20260216141302614](./assets/image-20260216141302614.png)

![image-20260216141336458](./assets/image-20260216141336458.png)

![image-20260216141356515](./assets/image-20260216141356515.png)

##### Output Style

**/output-style** lets you configure its personality and output i.e. default, explanatory, or learning. 

[Documentation](https://code.claude.com/docs/en/output-styles)

![image-20260216141622320](./assets/image-20260216141622320.png)

You can also create custom styles (md files) and put them at user level (~/.claude/output-styles) or project level (.claude/output-styles).

##### How Claude builds and tests iOS apps

It essentially uses **xcodebuild** to perform builds, then **xcrun simctl** to install and launch the app in sumulator, and take screenshots, **xdotool** ([link](https://github.com/jordansissel/xdotool)) to perform user gestures on the simulator, take more screenshots and save them, and finally writes a script to verify the screenshots. It places all of these screenshots and the script in `tmp` directory.

> The sample scripts are there in 'Verification Samples' folder.

![image-20260217132613855](./assets/image-20260217132613855.png)

Given that this is error-prone, I edited the Plan to just build the code and install the app. And then it gave me these as verification steps.

![image-20260217133334561](./assets/image-20260217133334561.png)