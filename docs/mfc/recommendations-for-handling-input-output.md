---
title: Recomendaciones para el control de entrada / salida
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 760c213c3af7f9c75374f04e3dfc6b9499eade5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218569"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recomendaciones para el control de entrada/salida

Si usa E/S de archivo o no depende de cómo responden a las preguntas en el árbol de decisión siguientes:

**¿Los datos principales en su aplicación residen en un archivo de disco**

- Sí, los datos principales residen en un archivo de disco:

     **La aplicación lee el archivo completo en la memoria en el archivo abierto y reescribir todo el archivo en el disco en para guardar archivos**

   - Sí: Este es el caso de documento MFC de forma predeterminada. Use `CDocument` serialización.

   - No: Esto suele ser el caso de basado en transacciones de actualización del archivo. Actualice el archivo en una base por transacción y no es necesario `CDocument` serialización.

- No, los datos principales no residen en un archivo de disco:

     **¿Los datos residen en un origen de datos ODBC**

   - Sí, los datos residen en un origen de datos ODBC:

         Use MFC's database support. The standard MFC implementation for this case includes a `CDatabase` object, as discussed in the article [MFC: Using Database Classes with Documents and Views](../data/mfc-using-database-classes-with-documents-and-views.md). The application might also read and write an auxiliary file — the purpose of the application wizard "both a database view and file support" option. In this case, you'd use serialization for the auxiliary file.

   - No, los datos no residen en un origen de datos ODBC.

         Examples of this case: the data resides in a non-ODBC DBMS; the data is read via some other mechanism, such as OLE or DDE.

         In such cases, you won't use serialization, and your application won't have Open and Save menu items. You might still want to use a `CDocument` as a home base, just as an MFC ODBC application uses the document to store `CRecordset` objects. But you won't use the framework's default File Open/Save document serialization.

Para admitir la apertura, guardar y guardar como comandos en el menú archivo, el marco de trabajo proporciona la serialización de documentos. Serialización lee y escribe datos, incluidos los objetos derivados de la clase `CObject`, un almacenamiento permanente a, normalmente un archivo de disco. La serialización es fácil de usar y actúa de muchas de sus necesidades, pero puede no ser apropiado en muchas aplicaciones de acceso a datos. Las aplicaciones de acceso a datos suelen actualizan datos en una base por transacción. Actualizan los registros afectados por la transacción en lugar de leer y escribir en un archivo de datos completa a la vez.

Para obtener información acerca de la serialización, vea [serialización](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Vea también

[Serialización: serialización frente a Base de datos de entrada/salida](../mfc/serialization-serialization-vs-database-input-output.md)
