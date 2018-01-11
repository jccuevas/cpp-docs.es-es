---
title: DEFINE_COMMAND_EX | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEFINE_COMMAND_EX
dev_langs: C++
helpviewer_keywords: DEFINE_COMMAND_EX macro
ms.assetid: d3e2ef20-1455-46d2-8499-8ab84bbb90a4
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 851b346c8fac955f1d82c0c43fdf75c4784ca04c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="definecommandex"></a>DEFINE_COMMAND_EX
Especifica el comando que se usará para crear el conjunto de filas cuando se usa el [CCommand](../../data/oledb/ccommand-class.md) clase. Es compatible con aplicaciones de Unicode y ANSI.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
DEFINE_COMMAND_EX(  
x  
,   
wszCommand  
 )  
  
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