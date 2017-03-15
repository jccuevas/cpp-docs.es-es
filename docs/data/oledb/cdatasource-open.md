---
title: "CDataSource::Open | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ATL::CDataSource::Open"
  - "ATL.CDataSource.Open"
  - "CDataSource::Open"
  - "CDataSource.Open"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Open (método)"
ms.assetid: a6d28bd1-799a-48ed-8993-5f82d1705b77
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CDataSource::Open
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre una conexión a un origen de datos con un moniker **CLSID**, **ProgID** o `CEnumerator`, o bien presenta al usuario un cuadro de diálogo del localizador.  
  
## Sintaxis  
  
```  
  
        HRESULT Open(  
   const CLSID& clsid,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CLSID& clsid,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   LPCTSTR szProgID,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   DBPROPSET* pPropSet = NULL,  
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(  
   const CEnumerator& enumerator,  
   LPCTSTR pName,  
   LPCTSTR pUserName = NULL,  
   LPCTSTR pPassword = NULL,  
   long nInitMode = 0   
) throw( );  
HRESULT Open(  
   HWND hWnd = GetActiveWindow( ),  
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET   
) throw( );  
HRESULT Open(   
   LPCWSTR szProgID,   
   DBPROPSET* pPropSet = NULL,   
   ULONG nPropertySets = 1   
) throw( );  
HRESULT Open(   
   LPCSTR szProgID,   
   LPCTSTR pName,   
   LPCTSTR pUserName = NULL,   
   LPCTSTR pPassword = NULL,   
   long nInitMode = 0   
) throw( );  
```  
  
#### Parámetros  
 `clsid`  
 \[in\] El **CLSID** del proveedor de datos.  
  
 *pPropSet*  
 \[in\] Un puntero a una matriz de estructuras [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) que contiene las propiedades y los valores que se van a establecer.  Vea [Conjuntos de propiedades y grupos de propiedades](https://msdn.microsoft.com/en-us/library/ms713696.aspx) en la *Referencia del programador OLE DB* de [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 *nPropertySets*  
 \[in\] El número de estructuras [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) pasadas en el argumento *pPropSet*.  
  
 *pName*  
 \[in\] El nombre de la base de datos con la que se va a conectar.  
  
 *pUserName*  
 \[in\] El nombre de usuario.  
  
 *pPassword*  
 \[in\] La contraseña del usuario.  
  
 `nInitMode`  
 \[in\] El modo de inicialización de la base de datos.  Vea [Propiedades de inicialización](https://msdn.microsoft.com/en-us/library/ms723127.aspx) en la *Referencia del programador de OLE DB* de [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener una lista de modos de inicialización válidos.  Si `nInitMode` es cero, no se incluye ningún modo de inicialización en el conjunto de propiedades que se usa para abrir la conexión.  
  
 `szProgID`  
 \[in\] Un identificador de programa.  
  
 `enumerator`  
 \[in\] Un objeto [CEnumerator](../../data/oledb/cenumerator-class.md) usado para obtener un moniker para abrir la conexión cuando el elemento que llama no especifica ningún **CLSID**.  
  
 `hWnd`  
 \[in\] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo.  Usar la sobrecarga de función que utiliza el parámetro `hWnd` invocará automáticamente a los componentes de servicio. Vea la sección Comentarios Para obtener más información.  
  
 `dwPromptOptions`  
 \[in\] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar.  Consulte los valores posibles en Msdasc.h.  
  
## Valor devuelto  
 Un `HRESULT` estándar.  
  
## Comentarios  
 La sobrecarga del método que usa el parámetro `hWnd` abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio como la agrupación de recursos y la inscripción automática de transacciones, entre otras.  Para obtener más información, vea "Servicios OLE DB" en la Referencia del programador de OLE DB de [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
 Las sobrecargas del método que no usan el parámetro `hWnd` abren un objeto de origen de datos sin utilizar los componentes del servicio en oledb32.dll.  Un objeto [CDataSource](../../data/oledb/cdatasource-class.md) abierto con estas sobrecargas de función no podrá usar ninguna de las funciones de los componentes del servicio.  
  
## Ejemplo  
 En el código siguiente se muestra cómo abrir un origen de datos de Jet 4.0 con plantillas OLE DB.  Trate el origen de datos de Jet como origen de datos OLE DB.  Sin embargo, la llamada a **Open** necesita dos conjuntos de propiedades: uno para **DBPROPSET\_DBINIT** y otro para **DBPROPSET\_JETOLEDB\_DBINIT**, de modo que pueda establecer **DBPROP\_JETOLEDB\_DATABASEPASSWORD**.  
  
 [!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/CPP/cdatasource-open_1.cpp)]  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)