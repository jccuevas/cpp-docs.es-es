---
title: CDataSource (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
dev_langs:
- C++
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69a96cf199e7ce131e91f750cdd83ebc915c38d8
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572684"
---
# <a name="cdatasource-class"></a>CDataSource (Clase)
Corresponde a un objeto de origen de datos OLE DB, que representa una conexión a través de un proveedor a un origen de datos.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CDataSource  
```  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h 
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[Cerrar](#close)|Cierra la conexión.|  
|[GetInitializationString](#getinitializationstring)|Recupera la cadena de inicialización del origen de datos que está abierto actualmente.|  
|[GetProperties](#getproperties)|Obtiene los valores de propiedades establecidas actualmente para el origen de datos conectado.|  
|[GetProperty](#getproperty)|Obtiene el valor de una propiedad única establecido actualmente para el origen de datos conectado.|  
|[Abrir](#open)|Crea una conexión a un proveedor (origen de datos) mediante un `CLSID`, `ProgID`, o un `CEnumerator` moniker proporcionado por el llamador.|  
|[OpenFromFileName](#openfromfilename)|Abre un origen de datos desde un archivo especificado por el nombre de archivo proporcionado por el usuario.|  
|[OpenFromInitializationString](#openfrominitializationstring)|Se abre el origen de datos especificado por una cadena de inicialización.|  
|[OpenWithPromptFileName](#openwithpromptfilename)|Permite al usuario seleccionar un archivo de vínculo de datos creado anteriormente para abrir el origen de datos correspondiente.|  
|[OpenWithServiceComponents](#openwithservicecomponents)|Abre un objeto de origen de datos mediante el cuadro de diálogo de vínculo de datos.|  
  
## <a name="remarks"></a>Comentarios  
 Una o varias sesiones de base de datos se pueden crear para una sola conexión. Estas sesiones se representan mediante `CSession`. Debe llamar a [CDataSource:: Open](../../data/oledb/cdatasource-open.md) para abrir la conexión antes de crear una sesión con `CSession::Open`.  
  
 Para obtener un ejemplo de cómo usar `CDataSource`, consulte el [CatDB](../../visual-cpp-samples.md) ejemplo.  

## <a name="close"></a> CDataSource:: Close
Cierra la conexión al liberar el `m_spInit` puntero.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
void Close() throw();  
``` 

## <a name="getinitializationstring"></a> CDataSource:: Getinitializationstring
Recupera la cadena de inicialización de un origen de datos que está abierto actualmente.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,   
   bool bIncludePassword = false) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pInitializationString*  
 [out] Un puntero a la cadena de inicialización.  
  
 *bIncludePassword*  
 [in] **true** si la cadena incluye una contraseña; de lo contrario **false**.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 La cadena de inicialización resultante puede utilizarse para posteriormente vuelve a abrir esta conexión de origen de datos. 
 
## <a name="getproperties"></a> CDataSource:: GetProperties
Devuelve la información de propiedad solicitada para el objeto de origen de datos conectado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetProperties(ULONG ulPropIDSets,   
   constDBPROPIDSET* pPropIDSet,   
   ULONG* pulPropertySets,   
   DBPROPSET** ppPropsets) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Consulte [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344\(v=vs.85\)) en el *referencia del programador OLE DB* en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener una propiedad única, utilice [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="getproperty"></a> CDataSource:: GetProperty
Devuelve el valor de una propiedad especificada para el objeto de origen de datos conectado.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetProperty(const GUID& guid,   
   DBPROPID propid,   
   VARIANT* pVariant) const throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *GUID*  
 [in] Un GUID que identifica el conjunto de propiedades para que se va a devolver la propiedad.  
  
 *PROPID*  
 [in] Identificador de propiedad para la propiedad para devolver.  
  
 *pVariant*  
 [out] Un puntero a la variante donde `GetProperty` devuelve el valor de la propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Para obtener varias propiedades, use [GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="open"></a> CDataSource:: Open
Abre una conexión a un origen de datos mediante un `CLSID`, `ProgID`, o `CEnumerator` moniker o pide al usuario con un cuadro de diálogo del localizador.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Open(const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  


HRESULT Open(const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,  
   LPCTSTR pName,  LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1) throw();  

HRESULT Open(const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0) throw();  

HRESULT Open(HWND hWnd = GetActiveWindow(),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,   
   DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,   
   LPCTSTR pName,LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *CLSID*  
 [in] El `CLSID` del proveedor de datos.  
  
 *pPropSet*  
 [in] Un puntero a una matriz de [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) estructuras que contienen las propiedades y valores que desea establecer. Consulte [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696\(v=vs.85\)) en el *referencia del programador OLE DB* en el SDK de Windows.  
  
 *nPropertySets*  
 [in] El número de [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) pasan las estructuras en el *pPropSet* argumento.  
  
 *pName*  
 [in] El nombre de la base de datos con la que se va a conectar.  
  
 *pUserName*  
 [in] El nombre de usuario.  
  
 *pPassword*  
 [in] La contraseña del usuario.  
  
 *nInitMode*  
 [in] El modo de inicialización de la base de datos. Consulte [propiedades de inicialización](/previous-versions/windows/desktop/ms723127\(v=vs.85\))en el *referencia del programador de OLE DB* en el SDK de Windows para obtener una lista de modos de inicialización válido. Si *nInitMode* es la inicialización cero, no se incluye el modo en el conjunto de propiedades utilizado para abrir la conexión.  
  
 *szProgID*  
 [in] Un identificador de programa.  
  
 *enumerator*  
 [in] Un [CEnumerator](../../data/oledb/cenumerator-class.md) objeto utilizado para obtener un moniker para abrir la conexión cuando el llamador no especifica un `CLSID`.  
  
 *hWnd*  
 [in] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo. Mediante la sobrecarga de función que usa el *hWnd* parámetro invocará automáticamente los componentes del servicio; vea la sección Comentarios para obtener más información.  
  
 *dwPromptOptions*  
 [in] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar. Consulte los valores posibles en Msdasc.h.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 La sobrecarga del método que utiliza el *hWnd* parámetro abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes del servicio como la agrupación de recursos, automático La inscripción en transacciones y así sucesivamente. Para obtener más información, vea "Servicios OLE DB" en referencia del programador de OLE DB en [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Las sobrecargas del método que no usan el *hWnd* parámetro abrir un objeto de origen de datos sin usar los componentes del servicio en oledb32.dll. Un [CDataSource](../../data/oledb/cdatasource-class.md) objeto abierto con estas sobrecargas de función no se puede usar cualquiera de la funcionalidad de los componentes de servicio.  
  
### <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo abrir un origen de datos de Jet 4.0 con plantillas OLE DB. Trate el origen de datos de Jet como origen de datos OLE DB. Sin embargo, la llamada a `Open` necesita dos conjuntos de propiedades: uno para DBPROPSET_DBINIT y otro para DBPROPSET_JETOLEDB_DBINIT, para que pueda establecer DBPROP_JETOLEDB_DATABASEPASSWORD.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  

## <a name="openfromfilename"></a> CDataSource:: Openfromfilename
Abre un origen de datos desde un archivo especificado por el nombre de archivo proporcionado por el usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *szFileName*  
 [in] El nombre de un archivo, normalmente una conexión de origen de datos. Archivo (.UDL).  
  
 Para obtener más información acerca de los archivos de vínculo de datos (archivos .udl), consulte [Introducción a la API de vínculo de datos](/previous-versions/windows/desktop/ms718102\(v=vs.85\)) en el SDK de Windows.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea "Servicios OLE DB" en referencia del programador de OLE DB en [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  

## <a name="openfrominitializationstring"></a> CDataSource:: OpenFromInitializationString
Se abre un origen de datos especificado por la cadena de inicialización proporcionada por el usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,   
   bool fPromptForInfo= false) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *szInitializationString*  
 [in] La cadena de inicialización.  
  
 *fPromptForInfo*  
 [in] Si este argumento se establece en **true**, a continuación, `OpenFromInitializationString` establecerá la propiedad DBPROP_INIT_PROMPT en DBPROMPT_COMPLETEREQUIRED, que especifica que se solicita al usuario solo si se necesita más información. Esto es útil para situaciones en que la cadena de inicialización especifica una base de datos que requiere una contraseña, pero la cadena no contiene la contraseña. El usuario se solicitará una contraseña (o cualquier otra información que falta) al intentar conectarse a la base de datos.  
  
 El valor predeterminado es **false**, que especifica que el usuario nunca sea solicitados (conjuntos de DBPROP_INIT_PROMPT en DBPROMPT_NOPROMPT).  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras.  

## <a name="openwithpromptfilename"></a> CDataSource:: Openwithpromptfilename
Este método muestra al usuario un cuadro de diálogo y después abre un origen de datos mediante el archivo especificado por el usuario.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),   
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,   
   LPCOLESTR szInitialDirectory = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *hWnd*  
 [in] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo.  
  
 *dwPromptOptions*  
 [in] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar. Consulte los valores posibles en Msdasc.h.  
  
 *szInitialDirectory*  
 [in] El directorio inicial para mostrar en el cuadro de diálogo del localizador.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea "Servicios OLE DB" en referencia del programador de OLE DB en [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).

## <a name="openwithservicecomponents"></a> CDataSource:: Openwithservicecomponents
Abre un objeto de origen de datos usando los componentes del servicio en oledb32.dll.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  

HRESULT OpenWithServiceComponents (LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *CLSID*  
 [in] El `CLSID` de un proveedor de datos.  
  
 *szProgID*  
 [in] Identificador de programa del proveedor de datos.  
  
 *pPropset*  
 [in] Un puntero a una matriz de [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) estructuras que contienen las propiedades y valores que desea establecer. Consulte [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696\(v=vs.85\)) en el *referencia del programador OLE DB* en el SDK de Windows. Si el objeto de origen de datos se inicializa, las propiedades tienen que pertenecer al grupo de propiedades Data Source. Si la misma propiedad se especifica más de una vez en *pPropset*, a continuación, qué valor se utiliza es específica del proveedor. Si *ulPropSets* es cero, se omite este parámetro.  
  
 *ulPropSets*  
 [in] El número de [DBPROPSET](/previous-versions/windows/desktop/ms714367\(v=vs.85\)) pasan las estructuras en el *pPropSet* argumento. Si es cero, el proveedor omite *pPropset*.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea "Servicios OLE DB" en referencia del programador de OLE DB en [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).    

## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)