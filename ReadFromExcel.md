> InputStream input = POIExample.class.getResourceAsStream( "qa.xls" );/FileInputStream
> > POIFSFileSystem fs = new POIFSFileSystem( input );
> > HSSFWorkbook wb = new HSSFWorkbook(fs);
> > HSSFSheet sheet = wb.getSheetAt(0);


> // Iterate over each row in the sheet
> Iterator rows = sheet.rowIterator();
> while( rows.hasNext() ) {
> > HSSFRow row = (HSSFRow) rows.next();
> > System.out.println( "Row #" + row.getRowNum() );


> // Iterate over each cell in the row and print out the cell's content
> Iterator cells = row.cellIterator();
> while( cells.hasNext() ) {
> > HSSFCell cell = (HSSFCell) cells.next();
> > System.out.println( "Cell #" + cell.getCellNum() );
> > switch ( cell.getCellType() ) {
> > > case HSSFCell.CELL\_TYPE\_NUMERIC:
> > > > System.out.println( cell.getNumericCellValue() );
> > > > break;

> > > case HSSFCell.CELL\_TYPE\_STRING:
> > > > System.out.println( cell.getStringCellValue() );
> > > > break;

> > > default:
> > > > System.out.println( "unsuported sell type" );
> > > > break;

> > }

> }

> }