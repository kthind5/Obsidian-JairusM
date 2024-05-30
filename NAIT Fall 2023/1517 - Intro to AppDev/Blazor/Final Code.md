```C#
void Main(){
List<Regions> results = Region_GetList();
    results.Dump();        
    int regionID = 1;    
    Regions dataRegion = Region_GetByID(regionID);        if (dataRegion!= null){  
        dataRegion.Dump();  
    }    
else    
   {       
    Console.WriteLine($"No results for the requested ID of {regionID}");  
   }
}
```

# LINQPAD Section
This is outside the `void Main()`
```linqpad
List<Regions> Region_GetList()  
{    IEnumerable<Regions> results = Regions.OrderBy(r => r.RegionDescription);    return results.ToList();  
}Regions Region_GetByID(int regionid){    Regions results = Regions.Where(r => r.RegionID == regionid).FirstOrDefault();        return results;  
}
```