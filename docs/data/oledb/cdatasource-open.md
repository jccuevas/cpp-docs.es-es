---
title: 'CDataSource:: Open | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
dev_langs:
- C++
helpviewer_keywords:
- Open method
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 438ed0d649319830201883421f7c2191b361b529
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdatasourceopen"></a>CDataSource::Open
Abre una conexión a un origen de datos mediante un **CLSID**, **ProgID**, o `CEnumerator` moniker o pide al usuario un cuadro de diálogo de localizador.  
  
## <a name="syntax"></a>Sintaxis  
  
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
 `clsid`  
 [in] El **CLSID** del proveedor de datos.  
  
 *pPropSet*  
 [in] Un puntero a una matriz de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) las estructuras que contienen propiedades y valores que desea establecer. Vea [conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en el *referencia del programador OLE DB* en el SDK de Windows.  
  
 *nPropertySets*  
 [in] El número de [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) estructuras pasan en el *pPropSet* argumento.  
  
 *pName*  
 [in] El nombre de la base de datos con la que se va a conectar.  
  
 *pUserName*  
 [in] El nombre de usuario.  
  
 *pPassword*  
 [in] La contraseña del usuario.  
  
 `nInitMode`  
 [in] El modo de inicialización de la base de datos. Vea [propiedades de inicialización](https://msdn.microsoft.com/en-us/library/ms723127.aspx)en el *referencia del programador de OLE DB* en el SDK de Windows para obtener una lista de modos de inicialización válido. Si `nInitMode` es cero, no se incluye ningún modo de inicialización en el conjunto de propiedades que se usa para abrir la conexión.  
  
 `szProgID`  
 [in] Un identificador de programa.  
  
 `enumerator`  
 [in] A [CEnumerator](../../data/oledb/cenumerator-class.md) objeto que se usa para obtener un moniker para abrir la conexión cuando el llamador no especifica un **CLSID**.  
  
 `hWnd`  
 [in] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo. Usar la sobrecarga de función que utiliza el parámetro `hWnd` invocará automáticamente a los componentes de servicio. Vea la sección Comentarios Para obtener más información.  
  
 `dwPromptOptions`  
 [in] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar. Consulte los valores posibles en Msdasc.h.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 La sobrecarga del método que usa el parámetro `hWnd` abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea "Servicios OLE DB" en referencia del programador de OLE DB de [http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Las sobrecargas del método que no usan el parámetro `hWnd` abren un objeto de origen de datos sin utilizar los componentes del servicio en oledb32.dll. A [CDataSource](../../data/oledb/cdatasource-class.md) objeto abierto con estas sobrecargas de función se podrá usar ninguna de las funciones de componentes del servicio.  
  
## <a name="example"></a>Ejemplo  
 En el código siguiente se muestra cómo abrir un origen de datos de Jet 4.0 con plantillas OLE DB. Trate el origen de datos de Jet como origen de datos OLE DB. Sin embargo, la llamada a **abiertos** necesita dos conjuntos de propiedades: uno para **DBPROPSET_DBINIT** y otro para **DBPROPSET_JETOLEDB_DBINIT**, de modo que puede establecer  **DBPROP_JETOLEDB_DATABASEPASSWORD**.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataSource (Clase)](../../data/oledb/cdatasource-class.md)
