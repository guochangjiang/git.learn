git add

һ��ǰ��
git add������Ҫ���ڰ�����Ҫ�ύ���ļ�����Ϣ��ӵ��������С�������ʹ��git commitʱ��git�������������е������������ļ����ύ��
��������
git add ��ʾ add to index only files created or modified and not those deleted 
��ͨ����ͨ��git add ����ʽ��������ӵ��������У��������ļ�Ҳ������Ŀ¼��
git�������жϳ��У��޸ģ���������ɾ�������ļ��������жϳ�������ļ����������ǵ���Ϣ��ӵ��������С�
����git add -u
git add -u ��ʾ add to index only files modified or deleted and not those created 
git add -u []: ��������tracked�ļ��б��޸Ĺ�����ɾ���ļ�����Ϣ��ӵ������⡣�����ᴦ��untracted���ļ���
ʡ�Ա�ʾ.,����ǰĿ¼��
�ġ�git add -A
git add -A: []��ʾ��������tracked�ļ��б��޸Ĺ�����ɾ���ļ�������untracted���ļ���Ϣ��ӵ������⡣
ʡ�Ա�ʾ.,����ǰĿ¼��
�塢git add -i
���ǿ���ͨ��git add -i []����鿴�б������޸Ĺ�����ɾ���ļ���û���ύ���ļ���
��ͨ����revert��������Բ鿴������untracted���ļ���ͬʱ����һ��������ϵͳ��
���磺
 git add -i
           staged     unstaged path
  1:        +0/-0      nothing branch/t.txt
  2:        +0/-0      nothing branch/t2.txt
  3:    unchanged        +1/-0 readme.txt

*** Commands ***
  1: [s]tatus     2: [u]pdate     3: [r]evert     4: [a]dd untracked
  5: [p]atch      6: [d]iff       7: [q]uit       8: [h]elp
What now>
�����t.txt��t2.txt��ʾ�Ѿ���ִ����git add�����ύ�����Ѿ���ӵ��������С�
readme.txt��ʾ�Ѿ�����tracked�£������޸��ˣ����ǻ�û�б�ִ����git add������û��ӵ��������С�
5.1��revert������
����ͨ��git add -i��revert�����3: [r]evert�����Ѿ���ӵ��������е��ļ������������޳���
��3: [r]evert����ʾͨ��3��r��revert�ӻس�ִ�и����ִ�и������git�������������е��ļ��б�.
Ȼ��ͨ��������ѡ������"1"��ʾgit�������������е��ļ��б��еĵ�1���ļ���
"1-15"��ʾgit�������������е��ļ��б��еĵ�1���ļ�����15���ļ�.�س���ִ�С�
������ǲ������κζ�����ֱ�ӻس���������revert���������git add -i���������С�
5.2��update������
����ͨ��update�����2: [u]pdate�����Ѿ�tracked���ļ���ӵ��������С��������revert���������ơ�
5.3��add untracked������
ͨ��add untracked�����4: [a]dd untracked�����԰ѻ�û��git������ļ���ӵ��������С��������revert���������ơ�
5.4��diff������
����ͨ��diff�����6: [d]iff�����ԱȽ����������ļ���ԭ�汾�Ĳ��졣�������revert���������ơ�
5.5��status������
status������(1: [s]tatus)�����Ϻ�git add -i����
5.6��quit������
quit�����7: [q]uit�������˳�git add -i����ϵͳ
��������
���ǿ���ͨ��git add -h��������git add����İ����ĵ���
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