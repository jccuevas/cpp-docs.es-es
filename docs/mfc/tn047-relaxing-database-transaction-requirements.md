---
title: 'TN047: Reducir los requisitos de transacción de base de datos | Microsoft Docs'
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
ms.openlocfilehash: 96f3116f503ffa0ffc461ea2c1a0bdaf8947a0be
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427022"
---
# <a name="tn047-relaxing-database-transaction-requirements"></a>TN047: Reducir los requisitos de las transacciones de base de datos

Esta nota técnica, que describe los requisitos de transacción de las clases de base de datos ODBC de MFC, ahora está obsoleta. Antes de 4.2 de MFC, las clases de base de datos requiere que los cursores se conservan en conjuntos de registros después de un **CommitTrans** o **reversión** operación. Si el controlador ODBC y el DBMS no eran compatibles con este nivel de conservación de cursor, las clases de base de datos no habilitó las transacciones.

A partir de MFC 4.2, las clases de base de datos han relaja la restricción de que requiere la conservación del cursor. Si el controlador es compatible con ellos, se habilitará las transacciones. Sin embargo, ahora debe comprobar el efecto de un **CommitTrans** o **reversión** operación en conjuntos de registros abiertos. Consulte las funciones miembro [CDatabase:: GetCursorCommitBehavior](../mfc/reference/cdatabase-class.md#getcursorcommitbehavior) y [CDatabase:: GetCursorRollbackBehavior](../mfc/reference/cdatabase-class.md#getcursorrollbackbehavior) para obtener más información.

## <a name="see-also"></a>Vea también

[Notas técnicas por número](../mfc/technical-notes-by-number.md)<br/>
[Notas técnicas por categoría](../mfc/technical-notes-by-category.md)

