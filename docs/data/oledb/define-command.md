---
title: DEFINE_COMMAND | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEFINE_COMMAND
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND macro
ms.assetid: 9d724968-e242-413c-9a13-e7175fccf9b1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f95fafbd9a63c5bf31add8bad1a8757bdcb60ae1
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="definecommand"></a>DEFINE_COMMAND
Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Acepta solo los tipos de cadena que coincida con el tipo de aplicación especificado (ANSI o Unicode).  
  
> [!NOTE]
>  Se recomienda que use [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de `DEFINE_COMMAND`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
DEFINE_COMMAND(x, szCommand)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de la clase de registro (comando) del usuario.  
  
 `szCommand`  
 [in] La cadena de comandos que se usará para crear el conjunto de filas al usar [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Comentarios  
 La cadena de comandos que especifique se usará como valor predeterminado si no se especifica el texto de comando en el [CCommand:: Open](../../data/oledb/ccommand-open.md) método.  
  
 Esta macro acepta cadenas de ANSI si va a compilar la aplicación como ANSI o Unicode cadenas si va a compilar la aplicación como Unicode. Se recomienda que use [DEFINE_COMMAND_EX](../../data/oledb/define-command-ex.md) en lugar de `DEFINE_COMMAND`, ya que el primero acepta cadenas de Unicode, independientemente del tipo de aplicación ANSI o Unicode.  
  
## <a name="example"></a>Ejemplo  
 Vea [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)