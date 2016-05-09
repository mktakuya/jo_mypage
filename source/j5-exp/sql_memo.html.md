# SQLのメモ

## SQL文の試し方
jocalc1(2はダメよ)で、

```
psql -d h28_j5_g3
```

と入力して、PostgreSQLのコンソールにログインできます。

```
h28_j5_g3 =>
```

というプロンプトが表示されればログイン成功。

## 名前からコードを引く方法（車名、企業名、車種名）

コードはcodeカラムに、名前はnameカラムに入っています。

基本的に、○○名→○○コードは、

```
SELECT code FROM ○○ WHERE name = 'なんちゃら";
```

でいけます。

### 企業名から企業名コードを引く

```
SELECT code FROM company_names WHERE name = 'daihatsu';
```

### 車名から車名コードを引く

```
SELECT code FROM car_names WHERE name = 'ブーン';
```

### 車種から車種コードを引く

```
SELECT code FROM car_types WHERE name = 'コンパクト';
```

## 略語テーブルの扱い方
略語は abbrev_nameカラムに、正式名称はformal_nameカラムに入っています。

### 略語→正式名称

```
SELECT formal_name FROM terms WHERE abbrev_name = 'FF';
```

### 正式名称 → 略語

```
SELECT abbrev_name FROM terms WHERE formal_name = 'フロントエン
ジン・フロントドライブ';
```

## いろいろな検索
### 企業名検索
企業名コードが'1'（つまりdaihatsu） な車の車名コードと外観写真を引く。

```
SELECT DISTINCT car_name_code, appearance_photo FROM specs WHERE company_name_code = 1;
```

後で書く

