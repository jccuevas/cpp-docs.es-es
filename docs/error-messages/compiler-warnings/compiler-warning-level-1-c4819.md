---
title: Advertencia del compilador (nivel 1) C4819
ms.date: 04/08/2019
f1_keywords:
- C4819
helpviewer_keywords:
- C4819
ms.assetid: c0316e85-249c-414d-9df0-622d077c6bc2
ms.openlocfilehash: c9bf60e8eec0ee6416bda3323583f3e056fce1a8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174887"
---
# <a name="compiler-warning-level-1-c4819"></a>Advertencia del compilador (nivel 1) C4819

> El archivo contiene un carácter que no se puede representar en la página de códigos actual (*número*). Guarde el archivo en formato Unicode para evitar la pérdida de datos.

C4819 se produce al compilar un archivo de código fuente ANSI en un sistema mediante una página de códigos que no puede representar todos los caracteres del archivo.

Hay varias maneras de resolver C4819. Una manera sencilla es quitar el carácter infractor, si no es necesario, por ejemplo, si se encuentra en un comentario. Puede establecer la página de códigos del sistema en el panel de control en una que admita el juego de caracteres utilizado por el código fuente. Puede usar [secuencias de escape](/cpp/c-language/escape-sequences) Unicode para crear caracteres o cadenas que utilicen solo el juego básico de caracteres ANSI del código fuente. Por último, puede guardar el archivo en formato Unicode con una firma, también conocida como marca de orden de bytes (BOM).

Para guardar un archivo en formato Unicode, en Visual Studio, elija **archivo** > **Guardar como**. En el cuadro de diálogo **Guardar archivo como** , seleccione la lista desplegable del botón **Guardar** y elija **Guardar con codificación**. Si guarda en el mismo nombre de archivo, es posible que deba confirmar que desea reemplazar el archivo. En el cuadro de diálogo **Opciones avanzadas para guardar** , elija una codificación que pueda representar todos los caracteres del archivo (por ejemplo, **Unicode (UTF-8 con firma)-página de códigos 65001**y, a continuación, elija **Aceptar**.
