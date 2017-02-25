---
title: "CDataSource::OpenWithPromptFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource.OpenWithPromptFileName"
  - "OpenWithPromptFileName"
  - "ATL::CDataSource::OpenWithPromptFileName"
  - "ATL.CDataSource.OpenWithPromptFileName"
  - "CDataSource::OpenWithPromptFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenWithPromptFileName (método)"
ms.assetid: 89460504-1aaf-4412-aa7b-fa5a4b39ada3
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDataSource::OpenWithPromptFileName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este método muestra al usuario un cuadro de diálogo y después abre un origen de datos mediante el archivo especificado por el usuario.  
  
## Sintaxis  
  
```  
  
        HRESULT OpenWithPromptFileName(   
   HWND hWnd = GetActiveWindow(   
   ),   
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,   
   LPCOLESTR szInitialDirectory = NULL    
) throw( );  
```  
  
#### Parámetros  
 `hWnd`  
 \[in\] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo.  
  
 `dwPromptOptions`  
 \[in\] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar.  Consulte los valores posibles en Msdasc.h.  
  
 *szInitialDirectory*  
 \[in\] El directorio inicial para mostrar en el cuadro de diálogo del localizador.  
  
## Valor devuelto  
 Un `HRESULT` estándar.  
  
## Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras.  Para obtener más información, vea "Servicios OLE DB" en la Referencia del programador de OLE DB de [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)