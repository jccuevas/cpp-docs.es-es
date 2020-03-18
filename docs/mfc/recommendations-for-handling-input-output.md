---
title: Recomendaciones para el control de entrada-salida
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: 956a92fd1761f61081afa2eb9c6cb35fe72b46d6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446895"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recomendaciones para el control de entrada/salida

Tanto si utiliza e/s basada en archivos como si no depende de cómo responda a las preguntas en el siguiente árbol de decisión:

**Hace que los datos principales de la aplicación residan en un archivo de disco**

- Sí, los datos principales residen en un archivo de disco:

     **¿La aplicación lee el archivo completo en la memoria al abrir el archivo y vuelve a escribir el archivo completo en el disco al guardar el archivo?**

   - Sí: este es el caso de documento MFC predeterminado. Use la serialización `CDocument`.

   - No: suele ser el caso de la actualización basada en transacciones del archivo. El archivo se actualiza por transacción y no se necesita `CDocument` la serialización.

- No, los datos principales no residen en un archivo de disco:

     **¿Los datos residen en un origen de datos ODBC?**

   - Sí, los datos residen en un origen de datos ODBC:

      Usar la compatibilidad con bases de datos de MFC. La implementación estándar de MFC para este caso incluye un objeto `CDatabase`, como se describe en el artículo [MFC: usar clases de base de datos con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md). La aplicación también podría leer y escribir un archivo auxiliar, el propósito del Asistente para aplicaciones, como la opción vista de base de datos y compatibilidad con archivos. En este caso, usaría la serialización para el archivo auxiliar.

   - No, los datos no residen en un origen de datos ODBC.

      Ejemplos de este caso: los datos residen en un DBMS que no es de ODBC; los datos se leen a través de otro mecanismo, como OLE o DDE.

      En tales casos, no se utilizará la serialización y la aplicación no tendrá elementos de menú abrir y guardar. Es posible que desee seguir usando una `CDocument` como base de inicio, al igual que una aplicación ODBC de MFC utiliza el documento para almacenar objetos de `CRecordset`. Pero no utilizará el archivo predeterminado del marco de trabajo para la serialización de documentos abiertos/guardados.

Para admitir los comandos abrir, guardar y guardar como en el menú Archivo, el marco de trabajo proporciona la serialización de documentos. La serialización Lee y escribe datos, incluidos los objetos derivados de la clase `CObject`, en el almacenamiento permanente, normalmente un archivo de disco. La serialización es fácil de usar y sirve para muchas de sus necesidades, pero puede no ser adecuada en muchas aplicaciones de acceso a datos. Las aplicaciones de acceso a datos suelen actualizar los datos en cada transacción. Actualizan los registros afectados por la transacción en lugar de leer y escribir un archivo de datos completo a la vez.

Para obtener información sobre la serialización, vea [serialización](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Serialización: serialización frente a entrada/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md)
