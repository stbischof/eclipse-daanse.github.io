---
title: Minimal_Virtual_Cubes_With_Measures_only
group: Unstrutured
kind: other
number: z0
---
Virtual cube example with measures



## Definition

This files represent the complete definition of the catalog.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xmi:XMI xmi:version="2.0" xmlns:xmi="http://www.omg.org/XMI" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:roma="https://www.daanse.org/spec/org.eclipse.daanse.rolap.mapping">
  <roma:Catalog description="Schema of a minimal virtual cube with measures" name="Minimal_Virtual_Cubes_With_Measures_only" cubes="Cube1 Cube2 VirtualCubeMeasureOnly" dbschemas="databaseSchema"/>
  <roma:DatabaseSchema id="databaseSchema">
    <tables xsi:type="roma:PhysicalTable" id="C1_Fact" name="C1_Fact">
      <columns xsi:type="roma:PhysicalColumn" id="C1_Fact_KEY" name="KEY"/>
      <columns xsi:type="roma:PhysicalColumn" id="C1_Fact_VALUE" name="VALUE" type="Integer"/>
    </tables>
    <tables xsi:type="roma:PhysicalTable" id="C2_Fact" name="C2_Fact">
      <columns xsi:type="roma:PhysicalColumn" id="C2_Fact_KEY" name="KEY"/>
      <columns xsi:type="roma:PhysicalColumn" id="C2_Fact_VALUE" name="VALUE" type="Integer"/>
    </tables>
  </roma:DatabaseSchema>
  <roma:TableQuery id="c2TableQuery" table="C2_Fact"/>
  <roma:TableQuery id="c1TableQuery" table="C1_Fact"/>
  <roma:PhysicalCube id="Cube1" name="Cube1" query="c1TableQuery">
    <measureGroups>
      <measures xsi:type="roma:SumMeasure" id="C1-Measure-Sum" name="C1-Measure-Sum" column="C1_Fact_VALUE"/>
    </measureGroups>
  </roma:PhysicalCube>
  <roma:PhysicalCube id="Cube2" name="Cube2" query="c2TableQuery">
    <measureGroups>
      <measures xsi:type="roma:SumMeasure" id="C2-Measure-Sum" name="C2-Measure-Sum" column="C2_Fact_VALUE"/>
    </measureGroups>
  </roma:PhysicalCube>
  <roma:VirtualCube id="VirtualCubeMeasureOnly" name="VirtualCubeMeasureOnly" referencedMeasures="C1-Measure-Sum C2-Measure-Sum">
    <calculatedMembers name="Calculation1" formula="[Measures].[C1-Measure-Sum] + [Measures].[C2-Measure-Sum]"/>
    <cubeUsages cube="Cube1"/>
    <cubeUsages cube="Cube2"/>
  </roma:VirtualCube>
</xmi:XMI>

```



## Turorial Zip
This files contaisn the data-tables as csv and the mapping as xmi file.

<a href="./zip/tutorial.virtualcubemeasureonly.zip" download>Download Zip File</a>
