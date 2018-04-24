# csv2vcf
csv2vcf 是一个命令行工具（基于python）用于把 CSV 转换成 VCard (.vcf) 文件.

## 使用方法 :

终端输入 :

```
python csv2vcf.py CSV_FILE_NAME [ -s | --single ] INPUT_FILE_FORMAT
```

参数含义 :

- `CSV_FILE_NAME` 你想转换的CSV文件
- `INPUT_FILE_FORMAT` 一个JSON格式的描述字符串，告诉**csv2vcf**如何解析你的输入文件
- `-s` or `--single` : 默认情况下是输出单独的一个个vcf文件，如果设置了此参数会把所有转换结果整体输出到一个文件。


###### JSON 格式 :

JSON 对象可以有下面这些属性 :

`name`, `nickname`, `org`, `tel`, `tel2`, `tel3`, `tel4`, `tel5`, `tel6`, `url`, `bday`, `role`, `note`, 和 `email`, 每个属性对应 [vCard 属性类型](https://en.wikipedia.org/wiki/VCard)

JSON字符串格式：`{KEY_1:KEY_1_列号, KEY_2:KEY_2_列号, ...}`


###### 实例 :

假设你有一个CSV 叫`contacts.csv`，内容如下 :

```
+-----------+-------------+
|    NAME   |    MOBILE   |
+-----------+-------------+
|   Mrid    |  1111111111 |
|   Arnav   |  2222222222 |
|   Sunil   |  3333333333 |
|     .     |      .      |
|     .     |      .      |
|     .     |      .      |
+-----------+-------------+
```

要转换成 vCard, 你需要写 :

`python csv2vcf.py contacts.csv '{"name":1, "tel":2}'`

上面是会把每个联系人转换到单独的一个vcf文件。

如果你要生成单独的一个vcf文件，你需要写：

`python csv2vcf.py contacts.csv -s '{"name":1, "tel":2}'`


## Copyright and license :

The license is available within the repository in the [LICENSE](https://github.com/mridah/csv2vcf/blob/master/LICENSE.md) file.
