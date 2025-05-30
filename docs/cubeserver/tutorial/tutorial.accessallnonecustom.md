---
title: Cube_with_role_access_all_none_custom
group: Unstrutured
kind: other
number: z0
---
Cube with examples of roles with access (all, none, custom)
role4 use SchemaGrant, CubeGrant, HierarchyGrant, MemberGrant
Rollup policy: (Full. Partial. Hidden.)
Full. The total for that member includes all children. This is the default policy if you don't specify the rollupPolicy attribute.
Partial. The total for that member includes only accessible children.
Hidden. If any of the children are inaccessible, the total is hidden.



## Definition

This files represent the complete definition of the catalog.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<xmi:XMI xmi:version="2.0" xmlns:xmi="http://www.omg.org/XMI" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:roma="https://www.daanse.org/spec/org.eclipse.daanse.rolap.mapping">
  <roma:Catalog id="Cube_with_role_access_all_none_custom" description="Schema with role access all, none, custom" name="Cube_with_role_access_all_none_custom" cubes="Cube1 Cube2" accessRoles="role1 role11 role12 role2 role3 role3 manager role_u" dbschemas="databaseSchema"/>
  <roma:DatabaseSchema id="databaseSchema">
    <tables xsi:type="roma:PhysicalTable" id="Fact" name="Fact">
      <columns xsi:type="roma:PhysicalColumn" id="Fact_KEY" name="KEY"/>
      <columns xsi:type="roma:PhysicalColumn" id="Fact_VALUE" name="VALUE" type="Integer"/>
    </tables>
  </roma:DatabaseSchema>
  <roma:TableQuery id="Fact_Query" table="Fact"/>
  <roma:Level id="Level2" name="Level2" column="Fact_KEY"/>
  <roma:Hierarchy id="Hierarchy1" name="Hierarchy1" levels="Level2" primaryKey="Fact_KEY" query="Fact_Query"/>
  <roma:StandardDimension id="Dimension1" name="Dimension1" hierarchies="Hierarchy1"/>
  <roma:PhysicalCube id="Cube2" name="Cube2" query="Fact_Query">
    <dimensionConnectors foreignKey="Fact_KEY" dimension="Dimension1" overrideDimensionName="Dimension1"/>
    <measureGroups/>
  </roma:PhysicalCube>
  <roma:PhysicalCube id="Cube1" name="Cube1" query="Fact_Query">
    <dimensionConnectors foreignKey="Fact_KEY" dimension="Dimension1" overrideDimensionName="Dimension1" id="DimensionConnector1"/>
    <dimensionConnectors foreignKey="Fact_KEY" dimension="Dimension1" overrideDimensionName="Dimension2" id="DimensionConnector2"/>
    <measureGroups>
      <measures xsi:type="roma:SumMeasure" id="Measure1" name="Measure1" column="Fact_VALUE"/>
    </measureGroups>
  </roma:PhysicalCube>
  <roma:AccessRole id="role3" name="role3">
    <accessCatalogGrants catalogAccess="all"/>
  </roma:AccessRole>
  <roma:AccessRole id="role2" name="role2"/>
  <roma:AccessRole id="manager" name="manager">
    <accessCatalogGrants>
      <cubeGrants cubeAccess="all" cube="Cube1">
        <hierarchyGrants hierarchyAccess="custom" rollupPolicy="partial" hierarchy="Hierarchy1" topLevel="Level2">
          <memberGrants memberAccess="all" member="[Dimension1].[A]"/>
          <memberGrants member="[Dimension1].[B]"/>
        </hierarchyGrants>
        <hierarchyGrants hierarchyAccess="custom" hierarchy="Hierarchy1" bottomLevel="Level2" topLevel="Level2">
          <memberGrants memberAccess="all" member="[Dimension1].[A]"/>
          <memberGrants member="[Dimension1].[B]"/>
        </hierarchyGrants>
      </cubeGrants>
    </accessCatalogGrants>
  </roma:AccessRole>
  <roma:AccessRole id="role_u" name="role_u">
    <referencedAccessRoles id="role11" name="role11">
      <accessCatalogGrants>
        <cubeGrants cubeAccess="all" cube="Cube1"/>
      </accessCatalogGrants>
    </referencedAccessRoles>
    <referencedAccessRoles id="role12" name="role12">
      <accessCatalogGrants>
        <cubeGrants cubeAccess="all" cube="Cube2"/>
      </accessCatalogGrants>
    </referencedAccessRoles>
  </roma:AccessRole>
  <roma:AccessRole id="role1" name="role1">
    <accessCatalogGrants catalogAccess="all">
      <cubeGrants cube="Cube2"/>
    </accessCatalogGrants>
  </roma:AccessRole>
  <roma:AccessRole id="role3" name="role3">
    <accessCatalogGrants>
      <cubeGrants cubeAccess="all" cube="Cube1">
        <hierarchyGrants hierarchyAccess="custom" hierarchy="Hierarchy1" topLevel="Level2">
          <memberGrants memberAccess="all" member="[Dimension1].[A]"/>
          <memberGrants member="[Dimension1].[B]"/>
        </hierarchyGrants>
      </cubeGrants>
    </accessCatalogGrants>
  </roma:AccessRole>
</xmi:XMI>

```



## Turorial Zip
This files contaisn the data-tables as csv and the mapping as xmi file.

<a href="./zip/tutorial.accessallnonecustom.zip" download>Download Zip File</a>
