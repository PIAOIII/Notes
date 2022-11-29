[TOC]

```sql
CREATE [[GLOBAL] TEMPORARY] TABLE <表名定义> <表结构定义>;
<表名定义> ::= [<模式名>.] <表名> 
<表结构定义>::=<表结构定义1> | <表结构定义2>
<表结构定义1>::= (<列定义> {,<列定义>} [,<表级约束定义>{,<表级约束定义>}]) [<属性子句>][<压缩子句>][<高级日志子句>] [<add_log子句>] [<DISTRIBUTE子句>][<AUTO_INCREMENT子句>]
<表结构定义2>::=  [<属性子句>] [<压缩子句>]AS <不带INTO的SELECT语句>[<add_log子句>] [<DISTRIBUTE子句>];
<列定义> ::= <不同类型列定义> [<列定义子句>] [<STORAGE子句>][<存储加密子句>][COMMENT '<列注释>']
<不同类型列定义> ::=<普通列列定义>|<虚拟列列定义>
<普通列定义>::= <列名> <数据类型>
<虚拟列列定义> ::= <列名>[<数据类型>] [GENERATED ALWAYS]AS (<虚拟列定义>) [VIRTUAL] [VISIBLE]
<列定义子句> ::= 
	DEFAULT <列缺省值表达式> |
	<自增列子句> |
	<列级约束定义> |
	DEFAULT <列缺省值表达式> <列级约束定义> |
	<自增列子句> <列级约束定义> |
	<列级约束定义> DEFAULT <列缺省值表达式> |
	<列级约束定义> <自增列子句> 
<自增列子句> ::= IDENTITY [(<种子>,<增量>)]|
                  AUTO_INCREMENT
<列级约束定义> ::= <列级完整性约束>{,<列级完整性约束>}
<列级完整性约束> ::= [CONSTRAINT <约束名>] <column_constraint_action>[<失效生效选项>]
<column_constraint_action>::=
     [NOT] NULL |
     <唯一性约束选项> [USING INDEX TABLESPACE {<表空间名> | DEFAULT}]|
     <引用约束> |
     CHECK (<检验条件>)|
     NOT VISIBLE
<唯一性约束选项> ::= PRIMARY KEY | 
				  [NOT] CLUSTER PRIMARY KEY |
                  CLUSTER [UNIQUE] KEY | 
                  UNIQUE 
<引用约束> ::= [FOREIGN KEY] REFERENCES [PENDANT] [<模式名>.]<表名>[(<列名>{[,<列名>]})] [MATCH  <FULL|PARTIAL|SIMPLE>][<引用触发动作>] [WITH INDEX] 
<引用触发动作> ::=
	<UPDATE 规则> [<DELETE 规则>] |
	<DELETE 规则> [<UPDATE 规则>]
<UPDATE 规则> ::= ON UPDATE <引用动作>
<DELETE 规则> ::= ON DELETE <引用动作>
<引用动作> ::= CASCADE | SET NULL | SET DEFAULT | NO ACTION
<失效生效选项>::=ENABLE | DISABLE  

<STORAGE子句> ::= STORAGE(<STORAGE项> {,<STORAGE项>})
<STORAGE项> ::= 
	[INITIAL <初始簇数目>] |
	[NEXT <下次分配簇数目>] |
	[MINEXTENTS <最小保留簇数目>] |
	[ON <表空间名>] |
	[FILLFACTOR <填充比例>]|
	[BRANCH  <BRANCH数>]|
	[BRANCH  (<BRANCH数>, <NOBRANCH数>)]|
	[NOBRANCH]|
	[CLUSTERBTR]|
	[WITH COUNTER]|
	[WITHOUT COUNTER] |
    	[USING LONG ROW]
<存储加密子句> ::= <存储加密子句1>|<存储加密子句2>
<存储加密子句1> ::= ENCRYPT [<加密用法>|<加密用法><加密模式>|<加密模式>]
<存储加密子句2> ::= ENCRYPT < <加密用法>|<加密用法><加密模式>|<加密模式> ><散列选项>
<加密用法> ::= WITH <加密算法>
<加密模式> ::= <透明加密模式> | <半透明加密模式>
<透明加密模式> ::= AUTO
<半透明加密模式> ::= MANUAL
<散列选项> ::= HASH WITH [<密码引擎名>.]<散列算法> [<加盐选项>]
<加盐选项> ::= [NO] SALT

<表级约束定义>::=[CONSTRAINT <约束名>] <表级约束子句>[<失效生效选项>]
<表级约束子句>::=<表级完整性约束> 
<表级完整性约束> ::=
	<唯一性约束选项> (<列名> {,<列名>}) [USING INDEX TABLESPACE{ <表空间名> | DEFAULT}]|
	FOREIGN KEY (<列名>{,<列名>}) <引用约束> |
	CHECK (<检验条件>) 
<属性子句>::= <表空间子句>| 
            ON COMMIT <DELETE | PRESERVE>  ROWS| 
           <空间限制子句>| 
           <STORAGE子句>
<表空间子句>::=TABLESPACE <表空间名>
<空间限制子句> ::= 
	DISKSPACE LIMIT <空间大小>|
	DISKSPACE UNLIMITED
<压缩子句> ::= 
	COMPRESS | 
	COMPRESS (<列名> {,<列名>}) | 
	COMPRESS EXCEPT (<列名> {,<列名>})
<高级日志子句> ::= WITH ADVANCED LOG
<add_log子句>::= ADD LOGIC LOG
<DISTRIBUTE子句> ::= 
    DISTRIBUTED [RANDOMLY | FULLY]|
	DISTRIBUTED BY [<HASH>](<列名> {,<列名>})|
	DISTRIBUTED BY RANGE (<列名> {,<列名>})(<范围分布项> {,<范围分布项>})|
	DISTRIBUTED BY LIST (<<列名> {,<列名>}>)(<列表分布项> {,<列表分布项>})
<范围分布项> ::= 
		VALUES LESS THAN (<表达式>{,<表达式>}) ON <实例名>|
		VALUES EQU OR LESS THAN (<表达式>{,<表达式>}) ON <实例名>
 <列表分布项> ::= VALUES (<表达式>{,<表达式>}) ON <实例名>
<不带INTO的SELECT语句> ::= <查询表达式>|<带参数查询语句>
<带参数查询语句>::=<子查询>|(<带参数查询语句>)
<AUTO_INCREMENT子句>:：= AUTO_INCREMENT [=] <起始边界值>
```