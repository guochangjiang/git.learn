## git add�������
------------------------

### һ��ǰ��

`git add`������Ҫ���ڰ�����Ҫ�ύ���ļ�����Ϣ��ӵ��������С�������ʹ��`git commit`ʱ��git�������������е������������ļ����ύ��

### ��������

`git add <path>` ��ʾ `add to index only files created or modified and not those deleted `

Gitͨ����ͨ��`git add` ����ʽ��<path>��ӵ��������У�<path>�������ļ�Ҳ������Ŀ¼��git�������жϳ�<path>�У��޸ģ���������ɾ�������ļ��������жϳ�������ļ����������ǵ���Ϣ��ӵ��������С�

### ����git add -u

`git add -u` ��ʾ `add to index only files modified or deleted and not those created` 

`git add -u [<path>]`: ��<path>������tracked�ļ��б��޸Ĺ�����ɾ���ļ�����Ϣ��ӵ������⡣�����ᴦ��untracted���ļ���ʡ��<path>��ʾ.,����ǰĿ¼��

### �ġ�git add -A

`git add -A: [<path>]`��ʾ��<path>������tracked�ļ��б��޸Ĺ�����ɾ���ļ�������untracted���ļ���Ϣ��ӵ������⡣ʡ��<path>��ʾ.,����ǰĿ¼��

### �塢git add -i

���ǿ���ͨ��`git add -i [<path>]`����鿴�б������޸Ĺ�����ɾ���ļ���û���ύ���ļ�����ͨ����`revert`��������Բ鿴������untracted���ļ���ͬʱ����һ��������ϵͳ��

#### 5.1��revert������

����ͨ��`git add -i`��`revert`�����`3: [r]evert`�����Ѿ���ӵ��������е��ļ������������޳���

��`3: [r]evert`����ʾͨ��3��r��revert�ӻس�ִ�и����ִ�и������git�������������е��ļ��б�; Ȼ��ͨ��������ѡ������"1"��ʾgit�������������е��ļ��б��еĵ�1���ļ���"1-15"��ʾgit�������������е��ļ��б��еĵ�1���ļ�����15���ļ�.�س���ִ�С�

������ǲ������κζ�����ֱ�ӻس���������revert���������`git add -i`���������С�

#### 5.2��update������

����ͨ��update�����`2: [u]pdate`�����Ѿ�tracked���ļ���ӵ��������С��������revert���������ơ�

#### 5.3��add untracked������

ͨ��`add untracked`�����`4: [a]dd untracked`�����԰ѻ�û��git������ļ���ӵ��������С��������revert���������ơ�

#### 5.4��diff������

����ͨ��`diff`�����`6: [d]iff`�����ԱȽ����������ļ���ԭ�汾�Ĳ��졣�������revert���������ơ�

#### 5.5��status������
`status`������(`1: [s]tatus`)�����Ϻ�`git add -i`����

#### 5.6��quit������

`quit`�����`7: [q]uit`�������˳�`git add -i`����ϵͳ

��������
���ǿ���ͨ��`git add -h`��������`git ad`d����İ����ĵ���

```
git add -h
usage: git add [options] [--] ...
    -n, --dry-run         dry run
    -v, --verbose         be verbose

    -i, --interactive     interactive picking
    -p, --patch           select hunks interactively
    -e, --edit            edit current diff and apply
    -f, --force           allow adding otherwise ignored files
    -u, --update          update tracked files
    -N, --intent-to-add   record only the fact that the path will be added later
    -A, --all             add changes from all tracked and untracked files
    --refresh             don't add, only refresh the index
    --ignore-errors       just skip files which cannot be added because of errors
    --ignore-missing      check if - even missing - files are ignored in dry run
```