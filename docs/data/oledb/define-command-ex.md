---
title: DEFINE_COMMAND_EX | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: dae66cd7458eafd613c34fb03ac4b12f0962271f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Es compatible con aplicaciones de Unicode y ANSI.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
DEFINE_COMMAND_EX(x, wszCommand)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 *x*  
 [in] El nombre de la clase de registro (comando) del usuario.  
  
 `wszCommand`  
 [in] La cadena de comandos que se usará para crear el conjunto de filas al usar [CCommand](../../data/oledb/ccommand-class.md).  
  
## <a name="remarks"></a>Comentarios  
 La cadena de comandos que especifique se usará como valor predeterminado si no se especifica el texto de comando en el [CCommand:: Open](../../data/oledb/ccommand-open.md) método.  
  
 Esta macro acepta cadenas de Unicode, independientemente del tipo de aplicación. Esta macro es preferible [DEFINE_COMMAND](../../data/oledb/define-command.md) porque admite Unicode, así como aplicaciones ANSI.  
  
## <a name="example"></a>Ejemplo  
 Vea [BOOKMARK_ENTRY](../../data/oledb/bookmark-entry.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Macros y funciones globales para las plantillas de consumidor OLE DB](../../data/oledb/macros-and-global-functions-for-ole-db-consumer-templates.md)