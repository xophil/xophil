import requests

# ==========================
# CONFIGURATION
# ==========================
GITHUB_USERNAME = "sophilsthapit"
EMAIL = "sophilsthapit01@gmail.com"
LINKEDIN = "https://www.linkedin.com/in/sophil-sthapit/"
X_LINK = "https://x.com/thesilentsystm"
OS = "Linux Mint"
AGE = "21 years"
PROGRAMMING_LANGUAGES = "Python, JavaScript"
COMPUTER_LANGUAGES = "HTML"
REAL_LANGUAGES = "English, Nepali, Hindi, Newari"
HOBBIES = "Music, Art, Coding"
SVG_FILE = "profile.svg"

# ==========================
# FETCH GITHUB DATA
# ==========================
def get_github_stats(username):
    user_url = f"https://api.github.com/users/{username}"
    repos_url = f"https://api.github.com/users/{username}/repos?per_page=100"

    user_data = requests.get(user_url).json()
    repos_data = requests.get(repos_url).json()

    repo_count = user_data.get("public_repos", 0)

    total_commits = 0
    for repo in repos_data:
        repo_name = repo["name"]
        commits_url = f"https://api.github.com/repos/{username}/{repo_name}/commits?author={username}&per_page=1"
        # Use GitHub Link header to get total count from pagination
        r = requests.get(commits_url)
        if "Link" in r.headers:
            # Parse last page number
            links = r.headers["Link"].split(",")
            for link in links:
                if 'rel="last"' in link:
                    last_url = link.split(";")[0].strip()[1:-1]
                    total_commits += int(last_url.split("page=")[-1])
                    break
        else:
            total_commits += len(r.json())

    return repo_count, total_commits

repo_count, commit_count = get_github_stats(GITHUB_USERNAME)

# ==========================
# GENERATE SVG
# ==========================
svg_content = f"""<?xml version='1.0' encoding='UTF-8'?>
<svg xmlns="http://www.w3.org/2000/svg" font-family="ConsolasFallback,Consolas,monospace" width="985px" height="530px" font-size="16px">
<style>
@font-face {{
src: local('Consolas'), local('Consolas Bold');
font-family: 'ConsolasFallback';
font-display: swap;
-webkit-size-adjust: 109%;
size-adjust: 109%;
}}
.key {{fill: #953800;}}
.value {{fill: #0a3069;}}
.addColor {{fill: #1a7f37;}}
.delColor {{fill: #cf222e;}}
.cc {{fill: #c2cfde;}}
text, tspan {{white-space: pre;}}
</style>
<rect width="985px" height="530px" fill="#f6f8fa" rx="15"/>
<text x="15" y="30" fill="#24292f" class="ascii">
<tspan x="15" y="30">                                                  </tspan>
<tspan x="15" y="50">                                                  </tspan>
<tspan x="15" y="70">                                                  </tspan>
<tspan x="15" y="90">                                                  </tspan>
<tspan x="15" y="110">                                                  </tspan>
<tspan x="15" y="130">                                                  </tspan>
<tspan x="15" y="150">                                                  </tspan>
<tspan x="15" y="170">                                                  </tspan>
<tspan x="15" y="190">                                                  </tspan>
<tspan x="15" y="210">                                                  </tspan>
<tspan x="15" y="230">                                                  </tspan>
<tspan x="15" y="250">                                                  </tspan>
<tspan x="15" y="270">                                                  </tspan>
<tspan x="15" y="290">                                                  </tspan>
<tspan x="15" y="310">                                                  </tspan>
<tspan x="15" y="330">                                                  </tspan>
<tspan x="15" y="350">                                                  </tspan>
<tspan x="15" y="370">                                                  </tspan>
<tspan x="15" y="390">                                                  </tspan>
<tspan x="15" y="410">                                                  </tspan>
<tspan x="15" y="430">                                                  </tspan>
<tspan x="15" y="450">                                                  </tspan>
<tspan x="15" y="470">                                                  </tspan>
<tspan x="15" y="490">                                                  </tspan>
<tspan x="15" y="510">                                                  </tspan>
</text>
<text x="390" y="30" fill="#24292f">
<tspan x="390" y="30">{GITHUB_USERNAME}</tspan> -———————————————————————————————————————————-—-
<tspan x="390" y="50" class="cc">. </tspan><tspan class="key">OS</tspan>:<tspan class="cc"> ........................ </tspan><tspan class="value">{OS}</tspan>
<tspan x="390" y="70" class="cc">. </tspan><tspan class="key">Uptime</tspan>:<tspan class="cc"> ...................... </tspan><tspan class="value">{AGE}</tspan>
<tspan x="390" y="90" class="cc">. </tspan><tspan class="key">Languages</tspan>.<tspan class="key">Programming</tspan>:<tspan class="cc"> ..... </tspan><tspan class="value">{PROGRAMMING_LANGUAGES}</tspan>
<tspan x="390" y="110" class="cc">. </tspan><tspan class="key">Languages</tspan>.<tspan class="key">Computer</tspan>:<tspan class="cc"> ......... </tspan><tspan class="value">{COMPUTER_LANGUAGES}</tspan>
<tspan x="390" y="130" class="cc">. </tspan><tspan class="key">Languages</tspan>.<tspan class="key">Real</tspan>:<tspan class="cc"> ......................... </tspan><tspan class="value">{REAL_LANGUAGES}</tspan>
<tspan x="390" y="150" class="cc">. </tspan>
<tspan x="390" y="170" class="cc">. </tspan><tspan class="key">Hobbies</tspan>:<tspan class="cc"> .... </tspan><tspan class="value">{HOBBIES}</tspan>
<tspan x="390" y="210" class="cc">- Contact</tspan> -——————————————————————————————————————————————-—-
<tspan x="390" y="230" class="cc">. </tspan><tspan class="key">Email</tspan>:<tspan class="cc"> ..................................... </tspan><tspan class="value">{EMAIL}</tspan>
<tspan x="390" y="250" class="cc">. </tspan><tspan class="key">LinkedIn</tspan>:<tspan class="cc"> ...................................... </tspan><tspan class="value">{LINKEDIN}</tspan>
<tspan x="390" y="270" class="cc">. </tspan><tspan class="key">X</tspan>:<tspan class="cc"> ..................................................... </tspan><tspan class="value">{X_LINK}</tspan>
<tspan x="390" y="310" class="cc">- GitHub Stats</tspan> -—————————————————————————————————————————-—-
<tspan x="390" y="330" class="cc">. </tspan><tspan class="key">Repos</tspan>:<tspan class="cc"> ...................... </tspan><tspan class="value">{repo_count}</tspan>
<tspan x="390" y="350" class="cc">. </tspan><tspan class="key">Commits</tspan>:<tspan class="cc"> .................... </tspan><tspan class="value">{commit_count}</tspan>
</text>
</svg>
"""

# ==========================
# SAVE SVG FILE
# ==========================
with open(SVG_FILE, "w") as f:
    f.write(svg_content)

print(f"SVG profile generated: {SVG_FILE}")
