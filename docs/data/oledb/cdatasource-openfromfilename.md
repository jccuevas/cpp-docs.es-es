---
title: "CDataSource::OpenFromFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource::OpenFromFileName"
  - "ATL::CDataSource::OpenFromFileName"
  - "OpenFromFileName"
  - "CDataSource.OpenFromFileName"
  - "ATL.CDataSource.OpenFromFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenFromFileName (método)"
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# CDataSource::OpenFromFileName
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abre un origen de datos desde un archivo especificado por el nombre de archivo proporcionado por el usuario.  
  
## Sintaxis  
  
```  
  
        HRESULT OpenFromFileName(   
   LPCOLESTR szFileName    
) throw( );  
```  
  
#### Parámetros  
 `szFileName`  
 \[in\] El nombre de un archivo, normalmente una conexión de origen de datos. Archivo \(.UDL\).  
  
 Para obtener más información acerca de los archivos de vínculo de datos \(archivos .udl\), vea [Información general sobre la API de vínculos de datos](https://msdn.microsoft.com/en-us/library/ms718102.aspx) en el [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
## Valor devuelto  
 Un `HRESULT` estándar.  
  
## Comentarios  
 Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio como la agrupación de recursos y la inscripción automática de transacciones, entre otras.  Para más información, vea "Servicios OLE DB" en la Referencia del programador de OLE DB de [http:\/\/msdn.microsoft.com\/library\/default.asp?url\=\/library\/oledb\/htm\/oledbole\_db\_services.asp?frame\=true](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)