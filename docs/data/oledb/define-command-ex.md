---
title: "DEFINE_COMMAND_EX | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DEFINE_COMMAND_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DEFINE_COMMAND_EX (macro)"
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# DEFINE_COMMAND_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el comando que se utilizó para crear el conjunto de filas al utilizar la clase de [CCommand](../../data/oledb/ccommand-class.md) .  Admite Unicode y aplicaciones ANSI.  
  
## Sintaxis  
  
```  
  
DEFINE_COMMAND_EX(  
x  
,   
wszCommand  
 )  
  
```  
  
#### Parámetros  
 *x*  
 \[in\] El nombre de la clase de registro de usuario \(comando\).  
  
 `wszCommand`  
 \[in\] La cadena de comando que se utilizará para crear el conjunto de filas al utilizar [CCommand](../../data/oledb/ccommand-class.md).  
  
## Comentarios  
 La cadena de comando que especifique se utilizará como valor predeterminado si no especifica el texto del comando en el método de [CCommand::Open](../../data/oledb/ccommand-open.md) .  
  
 Esta macro acepta cadenas Unicode, independientemente del tipo de aplicación.  Esta macro es preferible a [DEFINE\_COMMAND](../../data/oledb/define-command.md) porque admite Unicode así como aplicaciones ANSI.  
  
## Ejemplo  
 Vea [BOOKMARK\_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## Requisitos  
 **Encabezado:** atldbcli.h  
  
## Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)