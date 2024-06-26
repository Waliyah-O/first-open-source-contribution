# Выпраўленні ў каміты

Уявіце, што вы зрабілі commit ў выдалены рэпазітар, а потым зразумелі, што дапусцілі памылку друку ў каментары да commit або забыліся ўставіць радок у гэты апошні па часе commit. Як паступіць у гэтай сітуацыі? Менавіта пра гэта і пойдзе гаворка ў гэтым дакуменце.

## Як змяніць каментар да нядаўняга камітаў пасля таго, як ён быў пасланы на Github (pushed)
Каб зрабіць гэта, не адкрываючы файл для рэдагавання,
* Набярыце ```git commit --amend -m "followed by your new commit message"```
* А затым выканаеце ```git push origin <branch-name>``` для таго, каб паслаць змены на Github.

Заўвага: Калі вы набярэце, толькі ```git commit --amend```, то адкрыецца тэкставы рэдактар і прапануе адрэдагаваць каментар да commit. 
Выкарыстанне ключа `` -m`` адмяняе запуск рэдактара.
 
## Як зрабіць змены ў адным commit

Што калі мы забыліся зрабіць невялікае змяненне ў файле, напрыклад, замяніць адно слова ў commit, які ўжо пасланы ў выдалены рэпазітар?

Хай, для прыкладу, запісы ў часопісе маіх commit выглядаюць наступным чынам:
`` `
g56123f create file bot file
a2235d updated contributor.md
a5da0d modified bot file
`` `
Дапусцім, я забыўся дадаць адно слова ў файл bot file

Ёсць два спосабу выправіць гэта. Першы заключаецца ў стварэнні новага commit, які змяшчае гэта змена, напрыклад, так:
`` `
g56123f create file botfile
a2235d updated contributor.md
a5da0d modified botfile
b0ca8f added single word to botfile
`` `
Другі спосаб складаецца ў выпраўленні камітаў a5da0d, даданні гэтага прапушчанага слова і запушивании гэтых змяненняў на Github ў выглядзе аднаго камітаў.
Другі спосаб ўяўляецца пераважнай, паколькі справа ідзе толькі аб нязначным змене.

Каб дамагчыся гэтага, мы паступім наступным чынам:
* Зменім файл. У дадзеным выпадку я змяню файл botfile, дадаўшы да яго слова, якое я прапусціў раней.
* Далей, праіндэксуем гэты файл пры дапамозе каманды ```git add <filename>```

У звычайным выпадку адразу пасля індэксавання мы робім `` `git commit -m" коментар да нашага commit "` ``, правільна? Але паколькі ў дадзеным выпадку наша задача - выправіць папярэдні commit, - то замест гэтага мы выканаем такую каманду:

* ```git commit --amend```
 У выніку адкрыецца акно тэкставага рэдактара, у якім мы маем магчымасць зрабіць змены ў каментары. Мы можам на самай справе адрэдагаваць каментар, ці пакінуць яго без зменаў.
* Выйдзем з рэдактара
* Запушим нашы змены пры дапамозе каманды ```git push origin <branch-name>```

Такім чынам, абодва выпраўлення апынуцца ў адным commit.