---
title: "CMyProviderSource (MyProviderDS.H) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - ""myproviderds.h""
  - "cmyprovidersource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMyProviderSource (clase): MyProviderDS.H"
  - "proveedores OLE DB, archivos generados por el asistente"
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMyProviderSource (MyProviderDS.H)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases de proveedor utilizan herencia múltiple.  El siguiente fragmento de código muestra la cadena de herencia para el objeto de origen de datos:  
  
```  
/////////////////////////////////////////////////////////////////////////  
// CMyProviderSource  
class ATL_NO_VTABLE CMyProviderSource :   
   public CComObjectRootEx<CComSingleThreadModel>,  
   public CComCoClass<CMyProviderSource, &CLSID_MyProvider>,  
   public IDBCreateSessionImpl<CMyProviderSource, CMyProviderSession>,  
   public IDBInitializeImpl<CMyProviderSource>,  
   public IDBPropertiesImpl<CMyProviderSource>,  
   public IPersistImpl<CMyProviderSource>,  
   public IInternalConnectionImpl<CMyProviderSource>  
```  
  
 Todos los componentes COM se derivan de `CComObjectRootEx` y `CComCoClass`.  `CComObjectRootEx` proporciona toda la implementación de la interfaz **IUnknown**.  Puede administrar cualquier modelo de subprocesos.  `CComCoClass` administra la compatibilidad con el control de errores.  Si desea enviar información más completa sobre los errores al cliente, puede utilizar algunas de las API para errores de `CComCoClass`.  
  
 El objeto de origen de datos también hereda de varias clases 'Impl'.  Cada clase proporciona la implementación de una interfaz.  El objeto de origen de datos implementa las interfaces `IPersist`, `IDBProperties`, **IDBInitialize** y **IDBCreateSession**.  OLE DB requiere cada interfaz para implementar el objeto de origen de datos.  Puede elegir ofrecer o no una funcionalidad concreta heredando o no desde una de estas clases 'Impl'.  Si desea proporcionar compatibilidad con la interfaz **IDBDataSourceAdmin**, debe heredar de la clase **IDBDataSourceAdminImpl** para obtener la funcionalidad necesaria.  
  
## Mapa COM  
 Siempre que el cliente llame a `QueryInterface` para una interfaz en el origen de datos, recorre el mapa COM que se muestra a continuación:  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 Las macros COM\_INTERFACE\_ENTRY pertenecen a ATL e indican a la implementación de `QueryInterface` en `CComObjectRootEx` que devuelva las interfaces apropiadas.  
  
## Mapa de propiedades  
 El mapa de propiedades especifica todas las propiedades designadas por el proveedor:  
  
```  
BEGIN_PROPSET_MAP(CMyProviderSource)  
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)  
      PROPERTY_INFO_ENTRY(ACTIVESESSIONS)  
      PROPERTY_INFO_ENTRY(ASYNCTXNABORT)  
      PROPERTY_INFO_ENTRY(ASYNCTXNCOMMIT)  
      PROPERTY_INFO_ENTRY(BYREFACCESSORS)  
      PROPERTY_INFO_ENTRY_VALUE(CATALOGLOCATION, DBPROPVAL_CL_START)  
      PROPERTY_INFO_ENTRY(CATALOGTERM)  
      PROPERTY_INFO_ENTRY(CATALOGUSAGE)  
      PROPERTY_INFO_ENTRY(COLUMNDEFINITION)  
      PROPERTY_INFO_ENTRY(CONCATNULLBEHAVIOR)  
      PROPERTY_INFO_ENTRY(DATASOURCENAME)  
      PROPERTY_INFO_ENTRY(DATASOURCEREADONLY)  
      PROPERTY_INFO_ENTRY(DBMSNAME)  
      PROPERTY_INFO_ENTRY(DBMSVER)  
      PROPERTY_INFO_ENTRY_VALUE(DSOTHREADMODEL, DBPROPVAL_RT_FREETHREAD)  
      PROPERTY_INFO_ENTRY(GROUPBY)  
      PROPERTY_INFO_ENTRY(HETEROGENEOUSTABLES)  
      PROPERTY_INFO_ENTRY(IDENTIFIERCASE)  
      PROPERTY_INFO_ENTRY(MAXINDEXSIZE)  
      PROPERTY_INFO_ENTRY(MAXROWSIZE)  
      PROPERTY_INFO_ENTRY(MAXROWSIZEINCLUDESBLOB)  
      PROPERTY_INFO_ENTRY(MAXTABLESINSELECT)  
      PROPERTY_INFO_ENTRY(MULTIPLEPARAMSETS)  
      PROPERTY_INFO_ENTRY(MULTIPLERESULTS)  
      PROPERTY_INFO_ENTRY(MULTIPLESTORAGEOBJECTS)  
      PROPERTY_INFO_ENTRY(MULTITABLEUPDATE)  
      PROPERTY_INFO_ENTRY(NULLCOLLATION)  
      PROPERTY_INFO_ENTRY(OLEOBJECTS)  
      PROPERTY_INFO_ENTRY(ORDERBYCOLUMNSINSELECT)  
      PROPERTY_INFO_ENTRY(OUTPUTPARAMETERAVAILABILITY)  
      PROPERTY_INFO_ENTRY(PERSISTENTIDTYPE)  
      PROPERTY_INFO_ENTRY(PREPAREABORTBEHAVIOR)  
      PROPERTY_INFO_ENTRY(PREPARECOMMITBEHAVIOR)  
      PROPERTY_INFO_ENTRY(PROCEDURETERM)  
      PROPERTY_INFO_ENTRY(PROVIDERNAME)  
      PROPERTY_INFO_ENTRY(PROVIDEROLEDBVER)  
      PROPERTY_INFO_ENTRY(PROVIDERVER)  
      PROPERTY_INFO_ENTRY(QUOTEDIDENTIFIERCASE)  
      PROPERTY_INFO_ENTRY(ROWSETCONVERSIONSONCOMMAND)  
      PROPERTY_INFO_ENTRY(SCHEMATERM)  
      PROPERTY_INFO_ENTRY(SCHEMAUSAGE)  
      PROPERTY_INFO_ENTRY(STRUCTUREDSTORAGE)  
      PROPERTY_INFO_ENTRY(SUBQUERIES)  
      PROPERTY_INFO_ENTRY(TABLETERM)  
      PROPERTY_INFO_ENTRY(USERNAME)  
   END_PROPERTY_SET(DBPROPSET_DATASOURCEINFO)  
   BEGIN_PROPERTY_SET(DBPROPSET_DBINIT)  
      PROPERTY_INFO_ENTRY(AUTH_PASSWORD)  
      PROPERTY_INFO_ENTRY(AUTH_PERSIST_SENSITIVE_AUTHINFO)  
      PROPERTY_INFO_ENTRY(AUTH_USERID)  
      PROPERTY_INFO_ENTRY(INIT_DATASOURCE)  
      PROPERTY_INFO_ENTRY(INIT_HWND)  
      PROPERTY_INFO_ENTRY(INIT_LCID)  
      PROPERTY_INFO_ENTRY(INIT_LOCATION)  
      PROPERTY_INFO_ENTRY(INIT_MODE)  
      PROPERTY_INFO_ENTRY(INIT_PROMPT)  
      PROPERTY_INFO_ENTRY(INIT_PROVIDERSTRING)  
      PROPERTY_INFO_ENTRY(INIT_TIMEOUT)  
   END_PROPERTY_SET(DBPROPSET_DBINIT)  
   BEGIN_PROPERTY_SET(DBPROPSET_DATASOURCE)  
      PROPERTY_INFO_ENTRY(CURRENTCATALOG)  
   END_PROPERTY_SET(DBPROPSET_DATASOURCE)  
   CHAIN_PROPERTY_SET(CMyProviderSession)  
END_PROPSET_MAP()  
```  
  
 Las propiedades de OLE DB están agrupadas.  El objeto de origen de datos tiene dos grupos de propiedades: uno para el conjunto **DBPROPSET\_DATASOURCEINFO** y otro para el conjunto **DBPROPSET\_DBINIT**.  El conjunto **DBPROPSET\_DATASOURCEINFO** corresponde a propiedades del proveedor y su origen de datos.  El conjunto **DBPROPSET\_DBINIT** corresponde a propiedades utilizadas en la inicialización.  Las Plantillas de proveedores OLE DB controlan estos conjuntos con las macros PROPERTY\_SET.  Las macros crean un bloque que contiene una matriz de propiedades.  Siempre que el cliente llame a la interfaz `IDBProperties`, el proveedor utiliza el mapa de propiedades.  
  
 En este caso, no será necesario implementar cada propiedad de la especificación.  Sin embargo, debe proporcionar compatibilidad con las propiedades necesarias; vea la especificación de conformidad de nivel 0 para obtener más información.  Si no desea ofrecer compatibilidad con una propiedad, puede quitarla del mapa.  Si desea proporcionarla, agréguela al mapa mediante una macro PROPERTY\_INFO\_ENTRY.  La macro corresponde a la estructura **UPROPINFO**, como se muestra en el siguiente fragmento de código:  
  
```  
struct UPROPINFO  
{  
   DBPROPID    dwPropId;  
   ULONG       ulIDS;  
   VARTYPE     VarType;  
   DBPROPFLAGS dwFlags;  
   union  
   {  
      DWORD dwVal;  
      LPOLESTR szVal;  
   };  
   DBPROPOPTIONS dwOption;  
};  
```  
  
 Cada elemento de la estructura representa información para controlar la propiedad.  Contiene un identificador **DBPROPID** para determinar el GUID y el Id. para la propiedad.  También contiene entradas para determinar el tipo y el valor de la propiedad.  
  
 Si desea cambiar el valor predeterminado de una propiedad \(tenga en cuenta que un consumidor puede modificar el valor de una propiedad modificable cuando lo desee\), puede utilizar las macros PROPERTY\_INFO\_ENTRY\_VALUE o PROPERTY\_INFO\_ENTRY\_EX.  Estas macros permiten especificar un valor para la propiedad correspondiente.  La macro PROPERTY\_INFO\_ENTRY\_VALUE es una anotación abreviada que permite modificar el valor.  La macro PROPERTY\_INFO\_ENTRY\_VALUE llama a la macro PROPERTY\_INFO\_ENTRY\_EX.  Esta macro permite agregar o modificar todos los atributos de la estructura **UPROPINFO**.  
  
 Si desea definir su propio conjunto de propiedades, puede agregarlo mediante una combinación BEGIN\_PROPSET\_MAP\/END\_PROPSET\_MAP adicional.  Debe definir un GUID para el conjunto de propiedades y después definir sus propias propiedades.  Si tiene propiedades específicas del proveedor, agréguelas a un nuevo conjunto de propiedades en lugar de utilizar un conjunto existente.  De esta forma, evitará problemas en las versiones posteriores de OLE DB.  
  
## Conjuntos de propiedades definidos por el usuario  
 Visual C\+\+ .NET ofrece compatibilidad con los conjuntos de propiedades definidas por el usuario.  Ya no tendrá que reemplazar **GetProperties** o `GetPropertyInfo`.  En su lugar, las plantillas detectan cualquier conjunto de propiedades definido por el usuario y lo agregan al objeto apropiado.  
  
 Si tiene un conjunto de propiedades definido por el usuario que debe estar disponible en la inicialización \(es decir, antes de que el consumidor llame a **IDBInitialize::Initialize**\), puede especificarlo mediante el marcador **UPROPSET\_USERINIT** junto con la macro BEGIN\_PROPERTY\_SET\_EX.  El conjunto de propiedades debe estar en el objeto de origen de datos para que esto funcione \(como requiere la especificación OLE DB\).  Por ejemplo:  
  
```  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)