---
title: Recomendaciones para el control de entrada y salida | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9ee88b7784abb6ca622e72a9dfb31efc39fa7816
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930945"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recomendaciones para el control de entrada/salida
Si se usa E/S basada en archivos o no depende de cómo responden a las preguntas del siguiente árbol de decisión:  
  
 **¿Los datos en la aplicación principales residen en un archivo de disco**  
  
-   Sí, los datos principales residen en un archivo de disco:  
  
     **La aplicación lee el archivo completo en la memoria en el archivo abierto y reescribir todo el archivo en el disco en guardado de archivo.**  
  
    -   Sí: Este es el caso de documento MFC predeterminado. Use `CDocument` serialización.  
  
    -   No: Normalmente es el caso de basado en transacciones de actualización del archivo. Actualizar el archivo en una base por transacción y no es necesario `CDocument` serialización.  
  
-   No, los datos principales no residen en un archivo de disco:  
  
     **¿Los datos residen en un origen de datos ODBC**  
  
    -   Sí, los datos residen en un origen de datos ODBC:  
  
         Usar compatibilidad de base de datos de MFC. La implementación estándar de MFC para este caso incluye un `CDatabase` de objeto, como se describe en el artículo [MFC: utilizar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md). La aplicación también podría leer y escribir un archivo auxiliar, el propósito del Asistente para la aplicación opción "admiten una vista de base de datos y el archivo". En este caso, podría utilizar la serialización para el archivo auxiliar.  
  
    -   No, los datos no residen en un origen de datos ODBC.  
  
         Ejemplos de este caso: los datos residen en un DBMS no ODBC; se leen los datos a través de algún otro mecanismo, como OLE o DDE.  
  
         En tales casos, no utilizar la serialización y la aplicación no ha abierto y guardar elementos de menú. Es posible que aún desea usar un `CDocument` como base principal, al igual que un ODBC de MFC aplicación utiliza el documento para almacenar `CRecordset` objetos. Pero no usan la serialización de documentos de abrir archivo/Guardar del marco de trabajo de forma predeterminada.  
  
 Para admitir la apertura, guardar y guardar como comandos en el menú archivo, el marco de trabajo proporciona la serialización de documentos. Serialización lee y escribe datos, incluidos los objetos derivados de la clase `CObject`, un almacenamiento permanente a, normalmente un archivo de disco. Serialización es fácil de usar y sirve de muchas de sus necesidades, pero puede no ser apropiado en muchas aplicaciones de acceso a datos. Las aplicaciones de acceso a datos suelen actualizan datos en una base por transacción. Actualizan los registros afectados por la transacción en lugar de leer y escribir en un archivo de datos entero a la vez.  
  
 Para obtener información acerca de la serialización, vea [serialización](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Vea también  
 [Serialización: Serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)
