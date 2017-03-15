---
title: "CDataSource::OpenFromInitializationString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CDataSource.OpenFromInitializationString"
  - "OpenFromInitializationString"
  - "CDataSource::OpenFromInitializationString"
  - "ATL::CDataSource::OpenFromInitializationString"
  - "ATL.CDataSource.OpenFromInitializationString"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OpenFromInitializationString (método)"
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# CDataSource::OpenFromInitializationString
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Abra un origen de datos especificado por la cadena de inicialización usuario\- proporcionada.  
  
## Sintaxis  
  
```  
  
      HRESULT OpenFromInitializationString(   
   LPCOLESTR szInitializationString,   
   bool fPromptForInfo = false    
) throw( );  
```  
  
#### Parámetros  
 *el szInitializationString*  
 \[in\] La cadena de inicialización.  
  
 *fPromptForInfo*  
 \[in\] Si este argumento se establece en **true**, después `OpenFromInitializationString` establecerá la propiedad de **DBPROP\_INIT\_PROMPT** a **DBPROMPT\_COMPLETEREQUIRED**, que especifica que se soliciten al usuario sólo si más información es necesaria.  Esto es útil en situaciones en las que la cadena de inicialización especifica una base de datos que requiere una contraseña, pero no contiene la contraseña.  Se pedirá al usuario una contraseña \(o cualquier otra información que falta\) al intentar conectarse a la base de datos.  
  
 El valor predeterminado es **false**, que especifica que no se soliciten al usuario \(los conjuntos **DBPROP\_INIT\_PROMPT** a **DBPROMPT\_NOPROMPT**\).  
  
## Valor devuelto  
 `HRESULT`estándar.  
  
## Comentarios  
 Este método abre un objeto de origen de datos mediante los componentes de servicio en oledb32.dll; esta DLL contiene la implementación de las características de los componentes de Servicio como agrupación de recursos, alistamiento automático de transacciones, etc.  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [CDataSource \(Clase\)](../../data/oledb/cdatasource-class.md)