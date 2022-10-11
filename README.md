# api_yamdb

![SQLite](https://img.shields.io/badge/sqlite-%2307405e.svg?style=for-the-badge&logo=sqlite&logoColor=white)
![Django](https://img.shields.io/badge/django-%23092E20.svg?style=for-the-badge&logo=django&logoColor=white)
![DjangoREST](https://img.shields.io/badge/DJANGO-REST-ff1709?style=for-the-badge&logo=django&logoColor=white&color=ff1709&labelColor=gray)
![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)

<h2 align="center">��������</h2>
��������� ������ YaMDb.
��������������� ������� ���������������� ������������ REDOC.

API ��������� �� ������ ���� ������������, ��� �� ��� ������� ��� ��.

������������ ����� ����� �� ������: <a href="https://github.com/Rejden2000/api_yamdb/blob/master/api_yamdb/static/redoc.yaml">api_yamdb/api_yamdb/static/redoc.yaml</a>

������ ������ ����������� api ��� ��������� ������������, ����������� � ������ � ���.
����������� ���� ������� ���� �������. ����������� � ��������� ������ �� ���� �� �����.

������� �������� ������:

������ ����������� ����� ��� �����, ���������� ���������� �������������� (Auth � Users): ������� ����������� � ��������������, ����� �������, ������ � �������, ������� ������������� ����� e-mail.

������ ����������� ����� ��������� (Categories), ����� (Genres) � ������������ (Title): ������, ������������� � ��������� ��� ���.

������ ����������� ���������� �������� (Review) � ������������� (Comments): ��������� ������, �������������, ����������� ���������, ���������� ����� ������� ��� ��������. �������� ������������, � ����� ���������� ��������� ������� ������ �� csv ������, ���� ��������� �������� ������������.

��� �� ������ ��������� �����, ����������� ����� ������ �������, �������� ��������� � git, � ����� ������ �������� ������. 
��� ����� ������������ slug � ������.

����� ���� ����������� �������� ��������������, � ��������� ������ ��������.

<h2 align="center">����������</h2>

1. [���������](#����������)
2. [���� ����������](#����-����������)
3. [���������������� ����](#����������������-����)
4. [����� �������](#�����-�������)
5. [�������� �������](#��������-�������)

<h2 align="center">����������</h2>

����������� ����������� � ������� � ���� � ��������� ������:

```
git clone git@github.com:Rejden2000/api_yamdb.git
```

```
cd api_yamdb
```

C������ � ������������ ����������� ���������:

```
python3 -m venv env
```

```
source env/bin/activate
```

```
python3 -m pip install --upgrade pip
```

���������� ����������� �� ����� requirements.txt:

```
pip install -r requirements.txt
```

��������� ��������:

```
python3 manage.py migrate
```

��������� ������ ������� ������ �� ������ csv � ���� ������:

```
python3 manage.py importdata
```

��������� ������:

```
python3 manage.py runserver
```

<h2 align="center">���� ����������</h2>
<li><a href="https://www.djangoproject.com/">django 2.2</a></li>
<li><a href="https://www.django-rest-framework.org/">django rest framewor 3.12</a></li>
<li><a href="https://pypi.org/project/flake8/">flake8</a></li>
<li><a href="https://django-rest-framework-simplejwt.readthedocs.io/en/latest/">django rest framework simplejwt</a></li>
<li><a href="https://drf-yasg.readthedocs.io/en/stable/">drf-yasg</a></li>
<li><a href="https://django-filter.readthedocs.io/en/stable/">django filter</a></li>



<h2 align="center">���������������� ����</h2>

<li><strong>������.</strong> � ����� ������������� �������� ������������, ������ ������ � �����������.</li><br/>

<li><strong>������������������� ������������. (user)</strong> � ����� ����������� ������ � ������� ������ ������������� (�������/������/��������), ����� �������������� ������; ����� ������������� � ������� ���� ������ � �����������, ������������� ���� ������ ������������.</li><br/>

<li><strong>��������� (moderator).</strong> � ����� ������� � ������������� ����� ������ � �����������.</li><br/>

<li><strong>������������� (admin).</strong> � ������ ����� �� ���������� ���� ��������� �������.</li><br/>

<li><strong>�����������������.</strong> � ����� ��������� ���������������.</li><br/>

<h2 align="center">����� �������</h2>

<h3>��������������. ����������� ������������� � ������ �������:</h3>

���������������� ������ ������������. �������� ��� ������������� �� ���������� email.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/auth/signup/
```

��������� JWT-������. ��������� JWT-������ � ����� �� username � confirmation code.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/auth/token/
```

<h3>������������:</h3>

�������� ������ ���� �������������. �������� ������ ������������.

����� �������: <strong>�������������.</strong>

```
/api/v1/users/
```

�������� ������������ �� username. �������� ������ ������������ �� username. ������� ������������ �� username.

����� �������: <strong>�������������.</strong>

```
api/v1/users/{username}
```

�������� ������ ����� ������� ������. �������� ������ ����� ������� ������.

����� �������: <strong>����� �������������� ������������.</strong>

```
api/v1/users/me/
```

<h3>��������� (����) ������������ (��������, ������, �������):</h3>

�������� ������ ���� ���������.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/categories/
```

������� ���������.

����� �������: <strong>�������������.</strong>

```
api/v1/categories/
```

������� ���������.

����� �������: <strong>�������������.</strong>

```
api/v1/categories/{slug}/
```

<h3>����� ������������. ���� ������������ ����� ���� ��������� � ���������� ������:</h3>

�������� ������ ���� ������.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/genres/
```

�������� ����.

����� �������: <strong>�������������.</strong>

```
api/v1/genres/
```

������� ����.

����� �������: <strong>�������������.</strong>

```
api/v1/genres/{slug}/
```

<h3>������������, � ������� ����� ������ (����������� �����, ����� ��� �����):</h3>

�������� ������ ���� ������������.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/genres/
```

�������� ����� ������������.

����� �������: <strong>�������������.</strong>

```
api/v1/genres/
```

�������� ���������� � ������������.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/titles/{titles_id}/
```

�������� ���������� � ������������. ������� ������������.

����� �������: <strong>�������������.</strong>

```
api/v1/titles/{titles_id}/
```

<h3>������ �� ������������. ����� �������� � ������������ ������������:</h3>

�������� ������ ���� �������.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/titles/{titles_id}/
```

�������� ����� �����. ������������ ����� �������� ������ ���� ����� �� ������������.

����� �������: <strong>������������������� ������������.</strong>

```
api/v1/titles/{titles_id}/
```

�������� ����� �� id ��� ���������� ������������.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/
```

�������� �������� ����� �� id. ������� ����� �� id.

����� �������: <strong>����� ������, ��������� ��� �������������.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/
```

<h3>����������� � �������. ����������� �������� � ������������ ������.</h3>

�������� ������ ���� ������������ � ������ �� id.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/
```

�������� ����� ����������� ��� ������.

����� �������: <strong>������������������� ������������.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/
```

�������� ����������� ��� ������ �� id.

����� �������: <strong>�������� ��� ������.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```

�������� �������� ����������� � ������ �� id. ������� ����������� � ������ �� id.

����� �������: <strong>����� �����������, ��������� ��� �������������.</strong>

```
api/v1/titles/{title_id}/reviews/{review_id}/comments/{comment_id}/
```

<h2 align="center">�������� �������</h2>
<table>
  <tbody>
    <tr>
      <td align="center" valign="top">
        <img width="200" height="200" src="https://ca.slack-edge.com/TPV9DP0N4-U039Y2KLS6S-941cc7a2d585-512?s=150">
        <br>
        <a href="https://github.com/Rejden2000">����� ���������</a>
        <p>Team leader</p>
        <a href="https://hh.ru/resume/e1d7db7aff085eb8050039ed1f664e786a6334?from=share_ios">
          <img height="30px" src="https://i.hh.ru/logos/svg/hh.ru__min_.svg?v=11032019">
        </a>
        <a href="https://web.telegram.org/z/#969008307">
          <img height="30px" src="https://web.telegram.org/z/favicon.svg">
        </a>
        <br>
        <p>backend-developer</p>
      </td>
      <td align="center" valign="top">
        <img width="200" height="200" src="https://avatars.githubusercontent.com/u/54473049?v=4?s=150">
        <br>
        <a href="https://github.com/andpigge">������ �������</a>
        <p>Development</p>
        <a href="https://hh.ru/resume/dc361442ff07787a170039ed1f314a4e42476c">
          <img height="30px" src="https://i.hh.ru/logos/svg/hh.ru__min_.svg?v=11032019">
        </a>
        <br>
        <p>backend-developer</p>
      </td>
      <td align="center" valign="top">
        <img width="200" height="200" src="https://sun9-west.userapi.com/sun9-49/s/v1/ig2/WPfmcdC44tHUx4zU2kuFlrfK9P1dN1a30t1wB0R_OGOa40Vg2ee5y6YAS7H9AnPWcIjPpwK_bchEU4on36EyW3EI.jpg?size=2165x2160&quality=96&type=album?s=150">
        <br>
        <a href="https://github.com/RVG1995">����� ���������</a>
        <p>Development</p>
        <a href="https://ekaterinburg.hh.ru/resume/446324f9ff0b4c2d310039ed1f6a5657434130">
          <img height="30px" src="https://i.hh.ru/logos/svg/hh.ru__min_.svg?v=11032019">
        </a>
        <br>
        <p>backend-developer</p>
      </td>
     </tr>
  </tbody>
</table>
