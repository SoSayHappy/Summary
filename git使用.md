## git ����

* �������زֿ�

```
git init
```

* ����Զ�ֿ̲�

```
// ���һ���µ� remote Զ�ֿ̲�
git remote add [remote-name] [url]
����git remote add origin https://github.com/you/yourpro.git
origin���൱�ڸ�Զ�ֿ̲�ı���
```

* �ӱ��زֿ���ɾ��

```
git rm file.txt         // �Ӱ汾�����Ƴ���ɾ���ļ�
git rm file.txt -cached // �Ӱ汾�����Ƴ�����ɾ��ԭʼ�ļ�
git rm -r xxx           // �Ӱ汾����ɾ��ָ���ļ���
```

* �ӱ��زֿ�������µ��ļ�

```
git add .               // ��������ļ�
git add file.txt        // ���ָ���ļ�
```

* �ύ���ѻ��������ύ�� HEAD ��

```
git commit -m "ע��"
```

* �ѱ����ύ push ��Զ�̷�����

```
git push [remote-name] [loca-branch]:[remote-branch]
����git push origin master:master
```

* �鿴״̬

```
git status
```

* ��Զ�̿��������µĸĶ�

```
pull = fetch + merge

git pull [remote-name] [branch]
����git pull origin master
```
