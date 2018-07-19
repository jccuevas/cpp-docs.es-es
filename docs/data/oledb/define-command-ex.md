---
title: DEFINE_COMMAND_EX | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- DEFINE_COMMAND_EX
dev_langs:
- C++
helpviewer_keywords:
- DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2a77fa0d6655edeee88df3c7c45e1936a766b40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101047"
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