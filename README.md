# sqlml-parser

sqlml-parser is a Python implementation of an SQL parser that effectively converts SQL statements into Abstract Syntax Trees (AST). By leveraging AST tree comparisons between two SQL queries, it becomes possible to achieve robust evaluation of text-to-SQL models.

## Quick Start

### Install
```sh
pip install sqlml-parser
```
### Parser SQL

```python
>> > from sqlml_parser.parser.mysql_parser import parser as mysql_parser
>> > mysql_parser.parse("select * from t")
Query(query_body=QuerySpecification(select=Select(distinct=False, select_items=[
    SingleColumn(expression=QualifiedNameReference(name=QualifiedName.of("*")))]),
                                    from_=Table(name=QualifiedName.of("t"), for_update=False), order_by=[], limit=0,
                                    offset=0, for_update=False, nowait_or_wait=False), order_by=[], limit=0, offset=0)
>> > from sqlml_parser.parser.oceanbase_parser import parser as oceanbase_parser
>> > oceanbase_parser.parse("select * from t")
Query(query_body=QuerySpecification(select=Select(distinct=False, select_items=[
    SingleColumn(expression=QualifiedNameReference(name=QualifiedName.of("*")))]),
                                    from_=Table(name=QualifiedName.of("t"), for_update=False), order_by=[], limit=0,
                                    offset=0, for_update=False, nowait_or_wait=False), order_by=[], limit=0, offset=0)
>> > from sqlml_parser.parser.odps_parser import parser as odps_parser
>> > odps_parser.parse("select * from t")
Query(query_body=QuerySpecification(select=Select(distinct=False, select_items=[
    SingleColumn(expression=QualifiedNameReference(name=QualifiedName.of("*")))]),
                                    from_=Table(name=QualifiedName.of("t"), for_update=False), order_by=[], limit=0,
                                    offset=0, for_update=False, nowait_or_wait=False), order_by=[], limit=0, offset=0)
```

### Format SQL
```python
>>> from sqlml_parser.format.formatter import format_sql
>>> from sqlml_parser.parser.mysql_parser import parser
>>> result=parser.parse("select * from t")
>>> format_sql(result)
'SELECT\n  *\nFROM\n  t'

```
## Getting Started with SQL Parser Development

Document: [SQL Parser Development Guide](https://github.com/khulnasoft-lab/sqlml-parser/blob/main/docs/docs-en/SQL%20Parser%20Development%20Guide.md)