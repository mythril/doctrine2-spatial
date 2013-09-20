# Symfony2 Install

## composer.json
    "require": {
    	...
        "mythril/doctrine2-spatial": "dev-master"

You will also have to change the version requirement of doctrine to at least 2.1:

        "doctrine/orm": ">=2.1",


## config.yml
You need to manually add the types and functions you use:

	doctrine:
	    dbal:
	        types:
	            geometry:   CrEOF\Spatial\DBAL\Types\GeometryType
	            point:      CrEOF\Spatial\DBAL\Types\Geometry\PointType
	            polygon:    CrEOF\Spatial\DBAL\Types\Geometry\PolygonType
	            linestring: CrEOF\Spatial\DBAL\Types\Geometry\LineStringType
	    orm:
	        dql:
	            numeric_functions:
	                st_contains:        CrEOF\Spatial\ORM\Query\AST\Functions\PostgreSql\STContains
	                st_distance:        CrEOF\Spatial\ORM\Query\AST\Functions\PostgreSql\STDistance
	                st_area:            CrEOF\Spatial\ORM\Query\AST\Functions\PostgreSql\STArea
	                st_length:          CrEOF\Spatial\ORM\Query\AST\Functions\PostgreSql\STLength
	                st_geomfromtext:    CrEOF\Spatial\ORM\Query\AST\Functions\PostgreSql\STGeomFromText
