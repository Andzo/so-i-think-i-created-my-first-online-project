> /
    * Gets the list for combo box.
    * 
    * @param session the session
    * @param lookUpName the look up name
    * @return the list for combo box
    * 
> > private static HashMap<String, String> getListForComboBox(Session session, String lookUpName) {
> > > logger.info("BofaOIMInterface  --> getListForComboBox()-->" + lookUpName + "**");
> > > HashMap<String, String> lookupValueMap = new HashMap<String, String>();
> > > HashMap<String, String> lookupValueMapToReturn = new LinkedHashMap<String, String>();
> > > tcResultSet lookUpResult = null;
> > > if (session instanceof OIMSession) {
> > > > OIMSession oimSession = (OIMSession) session;
> > > > tcLookupOperationsIntf lookupOpr = oimSession.lookupApiInitialize();
> > > > try {
> > > > > lookUpResult = lookupOpr.getLookupValues(lookUpName);

> > > > } catch (tcAPIException e) {**


> logger.error("getListForComboBox" + e);
> } catch (tcInvalidLookupException e) {

> logger.error("getListForComboBox" + e);
> }
> }
> lookupValueMap = convertLookUpIntoHashMap(lookUpResult);
> List

&lt;String&gt;

 listKey=new ArrayList

&lt;String&gt;

(lookupValueMap.keySet());
> List

&lt;String&gt;

 listValues=new ArrayList

&lt;String&gt;

(lookupValueMap.values());
> TreeSet

&lt;String&gt;

 tree=new TreeSet

&lt;String&gt;

(listValues);
> Object[.md](.md) sortedArray = tree.toArray();

> int size = sortedArray.length;


> System.out.println(listValues);

> for (int i=0; i<size; i++)
> {



> lookupValueMapToReturn.put(listKey.get((int)listValues.indexOf(sortedArray[i](i.md))), (String) sortedArray[i](i.md));

> }

> return lookupValueMapToReturn;
> }