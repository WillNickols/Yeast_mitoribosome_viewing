## yMRC1 to yMRC2 LSU alignment
```
load yMRC2_sep10_updatedChainID.cif
ssu_list = ["g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "AG", "AH", "AI", "AJ", "AK", "Z", "AA", "AB", "AC", "AD", "AE", "AF", "AL"]
lsu_list = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f"]
ssu_selection_string = "chain " + " or chain ".join(ssu_list)
lsu_selection_string = "chain " + " or chain ".join(lsu_list)
cmd.extract("sub_1", "yMRC1_sep9 and (%s)"%lsu_selection_string)
cmd.extract("sub_2", " yMRC2_sep10_updatedChainID and (%s)"%lsu_selection_string)
align sub_2, sub_1
cmd.extract("sub_3", "yMRC2_sep10_updatedChainID and (%s)"%ssu_selection_string)
matrix_copy sub_2, sub_3
select obj1, sub_1 or yMRC1_sep9
create obj1_obj, obj1
select obj2, sub_3 or sub_2
create obj2_obj, obj2
save yMRC2_aligned.cif, obj2_obj
```

## yMRC1 to 5MRC LSU alignment
```
load 5MRC.cif
ssu_list_yMRC = ["g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "AG", "AH", "AI", "AJ", "AK", "Z", "AA", "AB", "AC", "AD", "AE", "AF", "AL"]
lsu_list_yMRC = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d", "e", "f"]
ssu_list_5MRC = ["AA", "BB", "CC", "DD", "EE", "FF", "GG", "HH", "II", "JJ", "KK", "LL", "MM", "NN", "OO", "PP", "QQ", "RR", "SS", "TT", "UU", "VV", "WW", "XX", "YY", "ZZ", "11", "22", "33", "44", "55", "66", "77", "88", "aa"]
lsu_list_5MRC = ["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M", "N", "O", "P", "Q", "R", "S", "T", "U", "V", "W", "X", "Y", "Z", "0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "a", "b", "c", "d"]
ssu_selection_string_yMRC = "chain " + " or chain ".join(ssu_list_yMRC)
lsu_selection_string_yMRC = "chain " + " or chain ".join(lsu_list_yMRC)
ssu_selection_string_5MRC = "chain " + " or chain ".join(ssu_list_5MRC)
lsu_selection_string_5MRC = "chain " + " or chain ".join(lsu_list_5MRC)
cmd.extract("sub_1", "yMRC1_sep9 and (%s)"%lsu_selection_string_yMRC)
cmd.extract("sub_2", " 5MRC and (%s)"%lsu_selection_string_5MRC)
align sub_2, sub_1
cmd.extract("sub_3", "5MRC and (%s)"%ssu_selection_string_5MRC)
matrix_copy sub_2, sub_3
select obj1, sub_1 or yMRC1_sep9
create obj1_obj, obj1
select obj2, sub_3 or sub_2
create obj2_obj, obj2
save 5mrc_aligned.cif, obj2_obj
```

## yMRC1 to yMRC2 15S alignment
```
load yMRC2_sep10_updatedChainID.cif
cmd.extract("sub_1", "yMRC1_sep9 and chain AL")
cmd.extract("sub_2", "yMRC2_sep10_updatedChainID and chain AL")
align sub_2, sub_1
save yMRC1_15S.cif, sub_1
save yMRC2_15S.cif, sub_2
```

## yMRC1 to yMRC2 head alignment
```
load yMRC2_sep10_updatedChainID.cif
head_list_yMRC1 = ["h", "i", "k", "m", "o", "p", "s", "t", "y", "AI", "AJ", "AK"]
head_list_yMRC2 = ["h", "i", "k", "m", "o", "p", "s", "t", "y", "AI", "AJ", "AK"]
selection_string_yMRC1 = "chain " + " or chain ".join(head_list_yMRC1)
selection_string_yMRC2 = "chain " + " or chain ".join(head_list_yMRC2)
cmd.extract("sub_1", " yMRC1_sep9 and ((%s) or (chain AL and resi 981-1457))"%selection_string_yMRC1)
cmd.extract("sub_2", " yMRC2_sep10_updatedChainID and ((%s) or (chain AL and resi 981-1457))"%selection_string_yMRC2)
align sub_2, sub_1
save yMRC1_head.cif, sub_1
save yMRC2_head.cif, sub_2
```

## 5MRC to 5MRE head alignment
```
load 5MRE.cif
head_list_5MRC = ["BB", "CC", "EE", "GG", "II", "JJ", "MM", "NN", "SS", "WW", "XX", "YY", "cc", "77"]
head_list_5MRE = ["BB", "CC", "EE", "GG", "II", "JJ", "MM", "NN", "SS", "WW", "XX", "YY", "cc", "77"]
selection_string_5MRC = "chain " + " or chain ".join(head_list_5MRC)
selection_string_5MRE = "chain " + " or chain ".join(head_list_5MRE)
cmd.extract("sub_1", " 5MRC and ((%s) or (chain aa and resi 981-1457))"%selection_string_5MRC)
cmd.extract("sub_2", " 5MRE and ((%s) or (chain aa and resi 981-1457))"%selection_string_5MRE)
align sub_2, sub_1
save 5MRC_head.cif, sub_1
save 5MRE_head.cif, sub_2
```

## yMRC1 to yMRC2 SSU body alignment
```
load yMRC2_sep10_updatedChainID.cif
ssu_list = ["g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "AG", "AH", "AI", "AJ", "AK", "Z", "AA", "AB", "AC", "AD", "AE", "AF", "AL"]
head_list_yMRC = ["h", "i", "k", "m", "o", "p", "s", "t", "y", "AI", "AJ", "AK"]
body_list_yMRC = ["g", "j", "l", "n", "q", "r", "u", "v", "w", "x", "z", "AG", "AH", "Z", "AA", "AB", "AC", "AD", "AE", "AF"]
ssu_selection_string = "chain " + " or chain ".join(ssu_list)
cmd.extract("sub_2", "yMRC2_sep10_updatedChainID and (%s)"%ssu_selection_string)
body_selection_string = "chain " + " or chain ".join(body_list_yMRC)
cmd.extract("sub_3", "sub_1 and ((%s) or (chain AL and not (resi 981-1457)))"%body_selection_string)
cmd.extract("sub_4", "sub_2 and ((%s) or (chain AL and not (resi 981-1457)))"%body_selection_string)
align sub_4, sub_3
head_selection_string = "chain " + " or chain ".join(head_list_yMRC)
cmd.extract("sub_5", "sub_2 and ((%s) or (chain AL and resi 981-1457))" %head_selection_string)
matrix_copy sub_4, sub_5
select obj1, sub_1 or sub_3
create obj1_obj, obj1
select obj2, sub_4 or sub_5
create obj2_obj, obj2
save yMRC1_body_aligned.cif, obj1_obj
save yMRC2_body_aligned.cif, obj2_obj
```

## yMRC1 to 5MRC SSU body alignment
```
load 5MRC.cif
ssu_list_yMRC = ["g", "h", "i", "j", "k", "l", "m", "n", "o", "p", "q", "r", "s", "t", "u", "v", "w", "x", "y", "z", "AG", "AH", "AI", "AJ", "AK", "Z", "AA", "AB", "AC", "AD", "AE", "AF", "AL"]
ssu_list_5MRC = ["AA", "BB", "CC", "DD", "EE", "FF", "GG", "HH", "II", "JJ", "KK", "LL", "MM", "NN", "OO", "PP", "QQ", "RR", "SS", "TT", "UU", "VV", "WW", "XX", "YY", "ZZ", "11", "22", "33", "44", "55", "66", "77", "88", "aa"]
head_list_yMRC = ["h", "i", "k", "m", "o", "p", "s", "t", "y", "AI", "AJ", "AK"]
body_list_yMRC = ["g", "j", "l", "n", "q", "r", "u", "v", "w", "x", "z", "AG", "AH", "Z", "AA", "AB", "AC", "AD", "AE", "AF"]
head_list_5MRC = ["BB", "CC", "EE", "GG", "II", "JJ", "MM", "NN", "SS", "WW", "XX", "YY", "77", "cc"]
body_list_5MRC = ["AA", "DD", "FF", "HH", "KK", "LL", "OO", "PP", "QQ", "RR", "TT", "UU", "VV", "ZZ", "11", "22", "33", "44", "55", "66", "88"]
ssu_selection_string_yMRC = "chain " + " or chain ".join(ssu_list_yMRC)
ssu_selection_string_5MRC = "chain " + " or chain ".join(ssu_list_5MRC)
cmd.extract("sub_1", "yMRC1_sep9 and (%s)"%ssu_selection_string_yMRC)
cmd.extract("sub_2", "5MRC and (%s)"%ssu_selection_string_5MRC)
body_selection_string_yMRC = "chain " + " or chain ".join(body_list_yMRC)
body_selection_string_5MRC = "chain " + " or chain ".join(body_list_5MRC)
cmd.extract("sub_3", "sub_1 and ((%s) or (chain AL and not (resi 981-1457)))"%body_selection_string_yMRC)
cmd.extract("sub_4", "sub_2 and ((%s) or (chain aa and not (resi 981-1457)))"%body_selection_string_5MRC)
align sub_4, sub_3
head_selection_string_yMRC = "chain " + " or chain ".join(head_list_yMRC)
head_selection_string_5MRC = "chain " + " or chain ".join(head_list_5MRC)
cmd.extract("sub_5", "sub_2 and ((%s) or (chain aa and resi 981-1457))" %head_selection_string_5MRC)
matrix_copy sub_4, sub_5
select obj1, sub_1 or sub_3
create obj1_obj, obj1
select obj2, sub_4 or sub_5
create obj2_obj, obj2
save yMRC1_body_aligned_2.cif, obj1_obj
save 5MRC_body_aligned.cif, obj2_obj
```

## 5MRC to 5MRE SSU body alignment
```
load 5MRE.cif
ssu_list_5MRC = ["AA", "BB", "CC", "DD", "EE", "FF", "GG", "HH", "II", "JJ", "KK", "LL", "MM", "NN", "OO", "PP", "QQ", "RR", "SS", "TT", "UU", "VV", "WW", "XX", "YY", "ZZ", "11", "22", "33", "44", "55", "66", "77", "88", "aa"]
head_list_5MRC = ["BB", "CC", "EE", "GG", "II", "JJ", "MM", "NN", "SS", "WW", "XX", "YY", "77", "cc"]
body_list_5MRC = ["AA", "DD", "FF", "HH", "KK", "LL", "OO", "PP", "QQ", "RR", "TT", "UU", "VV", "ZZ", "11", "22", "33", "44", "55", "66", "88"]
ssu_selection_string_5MRC = "chain " + " or chain ".join(ssu_list_5MRC)
cmd.extract("sub_1", "5MRC and (%s)"%ssu_selection_string_5MRC)
cmd.extract("sub_2", "5MRE and (%s)"%ssu_selection_string_5MRC)
body_selection_string_5MRC = "chain " + " or chain ".join(body_list_5MRC)
cmd.extract("sub_3", "sub_1 and ((%s) or (chain AL and not (resi 981-1457)))"%body_selection_string_5MRC)
cmd.extract("sub_4", "sub_2 and ((%s) or (chain aa and not (resi 981-1457)))"%body_selection_string_5MRC)
align sub_4, sub_3
head_selection_string_5MRC = "chain " + " or chain ".join(head_list_5MRC)
cmd.extract("sub_5", "sub_2 and ((%s) or (chain aa and resi 981-1457))" %head_selection_string_5MRC)
matrix_copy sub_4, sub_5
select obj1, sub_1 or sub_3
create obj1_obj, obj1
select obj2, sub_4 or sub_5
create obj2_obj, obj2
save 5MRC_body_aligned_2.cif, obj1_obj
save 5MRE_body_aligned.cif, obj2_obj
```

## yMRC1 to yMRC2 head alignment by RNA
```
load yMRC2_sep10_updatedChainID.cif
head_list_yMRC1 = ["h", "i", "k", "m", "o", "p", "s", "t", "y", "AI", "AJ", "AK"]
head_list_yMRC2 = ["h", "i", "k", "m", "o", "p", "s", "t", "y", "AI", "AJ", "AK"]
selection_string_yMRC1 = "chain " + " or chain ".join(head_list_yMRC1)
selection_string_yMRC2 = "chain " + " or chain ".join(head_list_yMRC2)
cmd.extract("sub_1", " yMRC1_sep9 and ((%s) or (chain AL and resi 981-1457))"%selection_string_yMRC1)
cmd.extract("sub_2", " yMRC2_sep10_updatedChainID and ((%s) or (chain AL and resi 981-1457))"%selection_string_yMRC2)
cmd.extract("sub_3", "sub_1 and chain AL")
cmd.extract("sub_4", "sub_2 and chain AL")
align sub_4, sub_3
matrix_copy sub_4, sub_2
select obj1, sub_1 or sub_3
create obj1_obj, obj1
select obj2, sub_2 or sub_4
create obj2_obj, obj2
save yMRC1_head_RNA_aligned.cif, obj1_obj
save yMRC2_head_RNA_aligned.cif, obj2_obj
```

## 5MRC to 5MRE head alignment by RNA
```
load 5MRE.cif
head_list_5MRC = ["BB", "CC", "EE", "GG", "II", "JJ", "MM", "NN", "SS", "WW", "XX", "YY", "cc", "77"]
head_list_5MRE = ["BB", "CC", "EE", "GG", "II", "JJ", "MM", "NN", "SS", "WW", "XX", "YY", "cc", "77"]
selection_string_5MRC = "chain " + " or chain ".join(head_list_5MRC)
selection_string_5MRE = "chain " + " or chain ".join(head_list_5MRE)
cmd.extract("sub_1", " 5MRC and ((%s) or (chain aa and resi 981-1457))"%selection_string_5MRC)
cmd.extract("sub_2", " 5MRE and ((%s) or (chain aa and resi 981-1457))"%selection_string_5MRE)
cmd.extract("sub_3", "sub_1 and chain aa")
cmd.extract("sub_4", "sub_2 and chain aa")
align sub_4, sub_3
matrix_copy sub_4, sub_2
select obj1, sub_1 or sub_3
create obj1_obj, obj1
select obj2, sub_2 or sub_4
create obj2_obj, obj2
save 5MRC_head_RNA_aligned.cif, obj1_obj
save 5MRE_head_RNA_aligned.cif, obj2_obj
```