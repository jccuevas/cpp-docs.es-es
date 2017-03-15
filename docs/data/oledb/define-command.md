---
title: "DEFINE_COMMAND | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFINE_COMMAND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINE_COMMAND (macro)"
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# DEFINE_COMMAND
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el comando que se utilizó para crear el conjunto de filas al utilizar la clase de [CCommand](../../data/oledb/ccommand-class.md) .  Acepta solo los tipos de cadenas que coinciden con el tipo de aplicación especificado \(ANSI o Unicode\).  
  
> [!NOTE]
>  Se recomienda utilizar [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) en lugar de `DEFINE_COMMAND`.  
  
## Sintaxis  
  
```  
  
DEFINE_COMMAND(  
x  
,   
szCommand  
 )  
  
```  
  
#### Parámetros  
 *x*  
 \[in\] El nombre de la clase de registro de usuario \(comando\).  
  
 `szCommand`  
 \[in\] La cadena de comando que se utilizará para crear el conjunto de filas al utilizar [CCommand](../../data/oledb/ccommand-class.md).  
  
## Comentarios  
 La cadena de comando que especifique se utilizará como valor predeterminado si no especifica el texto del comando en el método de [CCommand::Open](../../data/oledb/ccommand-open.md) .  
  
 Esta macro acepta cadenas ANSI si compila la aplicación como ANSI, o cadenas Unicode si compila la aplicación como Unicode.  Se recomienda utilizar [DEFINE\_COMMAND\_EX](../../data/oledb/define-command-ex.md) en lugar de `DEFINE_COMMAND`, porque el anterior acepta cadenas Unicode, independientemente del tipo de aplicación ANSI o Unicode.  
  
## Ejemplo  
 Vea [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)