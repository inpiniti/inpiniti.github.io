---
title: windows cli
author: JUNG YoungKyun
date: 2023-03-09
category: 34 cli
layout: post
---

# mkdir

mkdir는 "make directory"의 약어로, CLI(Command Line Interface)에서 디렉토리(폴더)를 생성하는 명령어입니다.

mkdir 명령어는 기본적으로 하나 이상의 디렉토리를 생성할 수 있습니다. 만약 생성하려는 디렉토리가 하위 디렉토리를 가지고 있지 않은 경우, 명령어는 해당 디렉토리를 생성합니다.

mkdir 명령어를 사용할 때, 생성하려는 디렉토리의 이름과 생성하려는 경로를 함께 지정해야 합니다. 예를 들어, 다음과 같은 명령어를 사용하여 "test"라는 이름의 디렉토리를 /home/user/Documents 경로에 생성할 수 있습니다.

```
mkdir /home/user/Documents/test
```
만약 여러 개의 디렉토리를 생성하려면, 각 디렉토리 이름을 띄어쓰기로 구분하여 명령어를 작성하면 됩니다. 예를 들어, 다음과 같은 명령어를 사용하여 "test1", "test2", "test3"라는 이름의 디렉토리를 /home/user/Documents 경로에 생성할 수 있습니다.

```
mkdir /home/user/Documents/test1 /home/user/Documents/test2 /home/user/Documents/test3
```
또한, mkdir 명령어는 여러 옵션을 제공합니다. 가장 많이 사용되는 옵션은 "-p" 옵션으로, 이 옵션을 사용하면 중간 경로에 존재하지 않는 디렉토리도 함께 생성할 수 있습니다. 예를 들어, 다음과 같은 명령어를 사용하여 "/home/user/Documents/test4/test5/test6" 디렉토리를 생성할 수 있습니다.

```
mkdir -p /home/user/Documents/test4/test5/test6
```
위 명령어에서 "-p" 옵션을 사용했기 때문에, "/home/user/Documents/test4"와 "/home/user/Documents/test4/test5" 디렉토리가 먼저 생성되고, 이후 "/home/user/Documents/test4/test5/test6" 디렉토리가 생성됩니다.

마지막으로, mkdir 명령어는 파일 권한을 지정할 수 있는 옵션도 제공합니다. 예를 들어, 다음과 같은 명령어를 사용하여 "test"라는 이름의 디렉토리를 /home/user/Documents 경로에 생성하면서, 권한을 755로 설정할 수 있습니다.

```
mkdir -m 755 /home/user/Documents/test
```
위 명령어에서 "-m" 옵션을 사용하면 파일 권한을 지정할 수 있습니다. "755"는 파일 권한을 나타내는데, 7은 rwx(읽기, 쓰기, 실행)를 각각 나타냅니다. 따라서 755는 소유자에게는 읽기, 쓰기, 실행 권한을 부여하고, 그룹과 다른 사용자에게는 읽기와 실행 권한을 부여하는 권한 설정입니다.
                                                                 
이처럼 mkdir 명령어는 다양한 옵션을 제공하여 디렉토리를 생성하고 권한을 설정할 수 있습니다. CLI를 사용하는 경우, mkdir 명령어를 잘 활용하면 디렉토리를 효율적으로 생성하고 관리할 수 있습니다.

# rmdir

rmdir은 "remove directory"의 약어로, CLI(Command Line Interface)에서 디렉토리(폴더)를 삭제하는 명령어입니다.

rmdir 명령어는 기본적으로 빈 디렉토리를 삭제할 때 사용합니다. 따라서 만약 삭제하려는 디렉토리가 하위 디렉토리나 파일이 포함되어 있는 경우, rmdir 명령어는 오류 메시지를 출력하고 해당 디렉토리를 삭제하지 않습니다.

rmdir 명령어를 사용할 때, 삭제하려는 디렉토리의 이름과 경로를 함께 지정해야 합니다. 예를 들어, 다음과 같은 명령어를 사용하여 "/home/user/Documents/test"라는 이름의 디렉토리를 삭제할 수 있습니다.

```
rmdir /home/user/Documents/test
```
만약 여러 개의 디렉토리를 삭제하려면, 각 디렉토리 이름을 띄어쓰기로 구분하여 명령어를 작성하면 됩니다. 예를 들어, 다음과 같은 명령어를 사용하여 "test1", "test2", "test3"라는 이름의 디렉토리를 /home/user/Documents 경로에서 삭제할 수 있습니다.

```
rmdir /home/user/Documents/test1 /home/user/Documents/test2 /home/user/Documents/test3
```
또한, rmdir 명령어는 "-p" 옵션을 제공합니다. 이 옵션을 사용하면 중간 경로에 존재하는 빈 디렉토리도 함께 삭제할 수 있습니다. 예를 들어, 다음과 같은 명령어를 사용하여 "/home/user/Documents/test4/test5/test6" 디렉토리를 삭제할 수 있습니다.

```
rmdir -p /home/user/Documents/test4/test5/test6
```
위 명령어에서 "-p" 옵션을 사용했기 때문에, "/home/user/Documents/test4/test5"와 "/home/user/Documents/test4" 디렉토리도 함께 삭제됩니다.

마지막으로, rmdir 명령어는 파일 권한을 지정할 수 있는 "-m" 옵션도 제공합니다. 하지만, 일반적으로 rmdir 명령어를 사용하여 디렉토리를 삭제할 때는 권한 설정이 필요하지 않습니다.

이처럼 rmdir 명령어는 디렉토리를 삭제하는 명령어로, 빈 디렉토리를 효율적으로 삭제할 수 있습니다. 하지만, 삭제하려는 디렉토리가 하위 디렉토리나 파일을 포함하고 있을 경우에는 다른 명령어를 사용해야 합니다.

## rmdir /s
rmdir 로 삭제 하다 보면 "디렉터리가 비어 있지 않습니다." 라는 에러 메시지를 만날수도 있습니다.
이러한 경우 "/s" 옵션을 사용하면 됩니다.

```
rmdir /s /home/user/Documents/test4/test5/test6
```

"계속하시겠습니까?(Y/N)" 정도만 물어보고 삭제를 시켜 줍니다.