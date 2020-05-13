---
title: Recomendaciones para el manejo de la entrada y la salida
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [MFC], about I/O
- file-based I/O options
- I/O [MFC]
- I/O [MFC], options
- I/O [MFC], file-based options
ms.assetid: d664b175-3b4a-40c3-b14b-39de6b12e419
ms.openlocfilehash: c365120a385c440f09f0ee4c0a2fc52afb55834f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371739"
---
# <a name="recommendations-for-handling-inputoutput"></a>Recomendaciones para el control de entrada/salida

Si utiliza E/S basadas en archivos o no depende de cómo responda a las preguntas en el siguiente árbol de decisiones:

**¿Residen los datos principales de la aplicación en un archivo de disco**

- Sí, los datos principales residen en un archivo de disco:

   **¿La aplicación lee todo el archivo en la memoria en File Open y escribe todo el archivo de nuevo en el disco en File Save**

  - Sí: este es el caso de documento MFC predeterminado. Utilice `CDocument` la serialización.

  - No: Este suele ser el caso de la actualización basada en transacciones del archivo. Actualizar el archivo por transacción y no `CDocument` es necesario serializar.

- No, los datos principales no residen en un archivo de disco:

   **¿Residen los datos en un origen de datos ODBC**

  - Sí, los datos residen en un origen de datos ODBC:

      Use la compatibilidad de base de datos de MFC. La implementación estándar de `CDatabase` MFC para este caso incluye un objeto, como se describe en el artículo MFC: Uso de clases de base de datos [con documentos y vistas](../data/mfc-using-database-classes-with-documents-and-views.md). La aplicación también puede leer y escribir un archivo auxiliar — el propósito del asistente de aplicación "tanto una vista de base de datos como la compatibilidad con archivos". En este caso, usaría la serialización para el archivo auxiliar.

  - No, los datos no residen en un origen de datos ODBC.

      Ejemplos de este caso: los datos residen en un DBMS que no es ODBC; los datos se leen a través de algún otro mecanismo, como OLE o DDE.

      En tales casos, no usará la serialización y la aplicación no tendrá elementos de menú Abrir y Guardar. Es posible que desee usar una `CDocument` base como base, al igual `CRecordset` que una aplicación ODBC de MFC usa el documento para almacenar objetos. Pero no usará la serialización de documentos de apertura/guardado de archivos predeterminada del marco de trabajo.

Para admitir los comandos Abrir, Guardar y Guardar como en el menú Archivo, el marco de trabajo proporciona serialización de documentos. La serialización lee y escribe datos, `CObject`incluidos los objetos derivados de la clase , en el almacenamiento permanente, normalmente un archivo de disco. La serialización es fácil de usar y atiende muchas de sus necesidades, pero puede ser inapropiada en muchas aplicaciones de acceso a datos. Las aplicaciones de acceso a datos suelen actualizar los datos por transacción. Actualizan los registros afectados por la transacción en lugar de leer y escribir un archivo de datos completo a la vez.

Para obtener información acerca de la serialización, vea [Serialización](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Consulte también

[Serialización: Serialización frente a entrada/salida de bases de datos](../mfc/serialization-serialization-vs-database-input-output.md)
