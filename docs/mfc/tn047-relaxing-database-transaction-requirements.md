---
title: 'TN047: Reducir los requisitos de transacción de base de datos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.data
dev_langs:
- C++
helpviewer_keywords:
- TN047
ms.assetid: f93c51cf-a8c0-43d0-aa47-7bcb8333d693
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be5870efacb61d5c0bb74f85427c41f787d2edd6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380939"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: Reducir los requisitos de las transacciones de base de datos
Esta nota técnica, que describen los requisitos de transacción de las clases de base de datos ODBC de MFC, ahora está obsoleta. Antes de MFC 4.2, las clases de base de datos requiere que los cursores se conservan en conjuntos de registros después de un **CommitTrans** o **reversión** operación. Si el controlador ODBC y DBMS no admitía este nivel de conservación de cursor, las clases de base de datos no ha habilitado las transacciones.  
  
 Empezando por MFC 4.2, las clases de base de datos han relajado la restricción de que requiere la conservación del cursor. Las transacciones se habilitarán si el controlador es compatible con ellos. Sin embargo, ahora debe comprobar el efecto de un **CommitTrans** o **reversión** operación en conjuntos de registros abiertos. Vea las funciones miembro [CDatabase:: GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) y [CDatabase:: GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

