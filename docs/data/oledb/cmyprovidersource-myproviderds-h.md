---
title: CMyProviderSource (MyProviderDS.H) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- myproviderds.h
- cmyprovidersource
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
- CMyProviderSource class in MyProviderDS.H
ms.assetid: c143d48e-59c8-4f67-9141-3aab51859b92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 848f940c9aa974c838a4600235ab97d099bcbd06
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340155"
---
# <a name="cmyprovidersource-myproviderdsh"></a>CMyProviderSource (MyProviderDS.H)
Las clases de proveedor utilizan herencia múltiple. El código siguiente muestra la cadena de herencia para el objeto de origen de datos:  
  
```cpp
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
  
 Todos los componentes COM que se derivan de `CComObjectRootEx` y `CComCoClass`. `CComObjectRootEx` proporciona toda la implementación para el `IUnknown` interfaz. Puede controlar cualquier modelo de subprocesos. `CComCoClass` controla cualquier compatibilidad error requerida. Si desea enviar información de error más completa al cliente, puede usar algunas de la API de errores en `CComCoClass`.  
  
 También hereda el objeto de origen de datos de varias clases 'Impl'. Cada clase proporciona la implementación de una interfaz. Los datos del origen de objeto implementa la `IPersist`, `IDBProperties`, `IDBInitialize`, y `IDBCreateSession` interfaces. OLE DB requiere cada interfaz para implementar el objeto de origen de datos. Puede elegir admitir o no una funcionalidad concreta heredando o no heredar de una de estas clases 'Impl'. Si desea admitir la `IDBDataSourceAdmin` interfaz, heredan de la `IDBDataSourceAdminImpl` clase para obtener la funcionalidad necesaria.  
  
## <a name="com-map"></a>Mapa COM  
 Cada vez que el cliente llama a `QueryInterface` para una interfaz en el origen de datos, pasa por el siguiente mapa COM:  
  
```  
BEGIN_COM_MAP(CMyProviderSource)  
   COM_INTERFACE_ENTRY(IDBCreateSession)  
   COM_INTERFACE_ENTRY(IDBInitialize)  
   COM_INTERFACE_ENTRY(IDBProperties)  
   COM_INTERFACE_ENTRY(IPersist)  
   COM_INTERFACE_ENTRY(IInternalConnection)  
END_COM_MAP()  
```  
  
 Las macros COM_INTERFACE_ENTRY pertenecen a ATL e indican a la implementación de `QueryInterface` en `CComObjectRootEx` para devolver las interfaces adecuadas.  
  
## <a name="property-map"></a>Asignación de propiedad  
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
  
 Se agrupan las propiedades de OLE DB. El objeto de origen de datos tiene dos grupos de propiedades: uno para el DBPROPSET_DATASOURCEINFO conjunto y otro para el DBPROPSET_DBINIT establecido. El conjunto DBPROPSET_DATASOURCEINFO corresponde a las propiedades del proveedor y su origen de datos. El conjunto DBPROPSET_DBINIT corresponde a las propiedades utilizadas en la inicialización. Las plantillas de proveedor OLE DB controlan estos conjuntos con las macros PROPERTY_SET. Las macros de crean un bloque que contiene una matriz de propiedades. Cada vez que el cliente llama a la `IDBProperties` interfaz, el proveedor utiliza la asignación de propiedad.  
  
 No es necesario implementar todas las propiedades en la especificación. Sin embargo, debe admitir las propiedades necesarias; vea la especificación de conformidad de nivel 0 para obtener más información. Si no desea admitir una propiedad, puede quitarlo del mapa. Si desea admitir una propiedad, agregarla a la asignación mediante el uso de una macro PROPERTY_INFO_ENTRY. La macro corresponde a la `UPROPINFO` estructura tal como se muestra en el código siguiente:  
  
```cpp  
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
  
 Cada elemento de la estructura representa información para controlar la propiedad. Contiene un `DBPROPID` para determinar el GUID y el identificador de la propiedad. También contiene entradas para determinar el tipo y el valor de la propiedad.  
  
 Si desea cambiar el valor predeterminado de una propiedad (tenga en cuenta que un consumidor puede cambiar el valor de una propiedad de escritura en cualquier momento), puede utilizar la macro PROPERTY_INFO_ENTRY_VALUE o PROPERTY_INFO_ENTRY_EX. Estas macros le permiten especificar un valor para una propiedad correspondiente. La macro PROPERTY_INFO_ENTRY_VALUE es una notación abreviada que permite cambiar el valor. La macro PROPERTY_INFO_ENTRY_VALUE llama a la macro PROPERTY_INFO_ENTRY_EX. Esta macro permite agregar o cambiar todos los atributos en el `UPROPINFO` estructura.  
  
 Si desea definir su propio conjunto de propiedades, puede agregar uno mediante la realización de una combinación BEGIN_PROPSET_MAP/END_PROPSET_MAP adicional. Debe definir un GUID para el conjunto de propiedades y, a continuación, definir sus propias propiedades. Si tiene propiedades específicas del proveedor, agregue una nueva propiedad establecida en lugar de usar uno existente. Esto evita problemas en versiones posteriores de OLE DB.  
  
## <a name="user-defined-property-sets"></a>Conjuntos de propiedades definido por el usuario  
 Visual C++ admite conjuntos de propiedades definido por el usuario. No es necesario invalidar `GetProperties` o `GetPropertyInfo`. En su lugar, las plantillas de detectan cualquier conjunto de propiedades definido por el usuario y agregarlo al objeto adecuado.  
  
 Si tiene un conjunto de propiedades definido por el usuario que debe estar disponible en tiempo de inicialización (es decir, antes de que el consumidor llama a `IDBInitialize::Initialize`), puede especificarlo mediante el indicador UPROPSET_USERINIT junto con la macro BEGIN_PROPERTY_SET_EX. El conjunto de propiedades debe estar en el objeto de origen de datos para que funcione (tal y como requiere la especificación OLE DB). Por ejemplo:  
  
```cpp  
BEGIN_PROPERTY_SET_EX(DBPROPSET_MYPROPSET, UPROPSET_USERINIT)  
   PROPERTY_INFO_ENTRY(DBPROP_MYPROP)  
END_PROPERTY_SET_EX(DBPROPSET_MYPROPSET)  
```  
  
## <a name="see-also"></a>Vea también  
 [Archivos generados por el Asistente para proveedores](../../data/oledb/provider-wizard-generated-files.md)