---
layout: post
title: Heroku에 Flask App Deploy하기
categories: Flask
tags: ['Heroku', 'Flask']
---

### GitHub Repository에 Push 하기

> #### 1. GitHub에 Repository 만들기

> #### 2. `.gitignore` 파일 만들기
[.gitignore 자동 생성](https://gitignore.io/){: target="_blank"}

```
### Flask ###
instance/*
!instance/.gitignore
.webassets-cache
.env

### Flask.Python Stack ###
# Byte-compiled / optimized / DLL files
__pycache__/
*.py[cod]
*$py.class

# PyCharm 사용으로 인한 무시 항목 추가
.idea/
```
> #### 3. `README.md` 파일 만들기 

```markdown
## Flask Test App
```

> #### 4. Github Repository에 Push

```
$ git init
$ git remote add origin 'Github Repository'
$ git add .
$ git commit -m "Flask Test App"
$ git branch -M main
$ git push -u origin main
```

<br>

### Heroku Deploy 를 위한 준비

>#### 1. Heroku 회원 가입하기
[Heroku](https://www.heroku.com/){: target="_blnak"}

> #### 2. Dashboard 에서 `Create New App`

> #### 3. Deploy 탭에서 GitHub 선택하고 GitHub 계정 연결

> #### 4. PyCharm 에서 해당 가상 환경에 `gunicorn` 설치

> #### 5. 확장자가 없는 `Procfile` 을 프로젝트 폴더에 만들다.

공백도 맞추어서 작성한다. 
{:.warning}

```
web: gunicorn app:app
```

> #### 6. 가상 환경 설정 파일인 `requirments.txt` 파일을 만든다.

터미널 창에 (venv)가 활성화 되어있는지 확인한다.
{:.warning}
Mac은 `pip3` 명령어를 사용한다.
{:.warning}

```
(venv)$ pip freeze > requirments.txt
```
#### `requirments.txt` 예시
```
click==8.1.3
Flask==2.2.1
gunicorn==20.1.0
importlib-metadata==4.12.0
itsdangerous==2.1.2
Jinja2==3.1.2
MarkupSafe==2.1.1
Werkzeug==2.2.1
zipp==3.8.1
```

> #### 7. `runtime.txt` 파일을 만든다.

Python 버전에 따라 Heroku 에서 설정해주는 Python 버전이 다르다.
{:.warning}

[Heroku Python Runtime version](https://devcenter.heroku.com/articles/python-support#specifying-a-python-version){: target="_blank"}

> python-3.10.6 on all supported stacks (recommended)  
python-3.9.13 on all supported stacks  
python-3.8.13 on Heroku-18 and Heroku-20 only  
python-3.7.13 on Heroku-18 and Heroku-20 only  

#### `runtime.txt` 예시

```
python-3.10.6
```

> #### 8. 모든 파일을 GitHub Repository에 Push

```
$ git add .
$ git commit -m "Flask Test App"
$ git push -u origin main
```

<br>

### Heroku Deploy

> #### 1. Heroku Deploy 의 GitHub 에서 작업한 Repository 선택

> #### 2. Menual Deploy 에서 `Deploy Branch` 클릭

`main` branch 뿐이기 때문에 기본적으로 `main`이 선택되어 있다.
{:.info} 

> #### 3. 완료되면 하단에 있는 `View` 버튼을 클릭하거나 상단에 있는 `Open app` 버튼을 클릭한다.




