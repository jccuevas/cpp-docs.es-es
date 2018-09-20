---
title: Inclusión de recursos de cuadro de diálogo) (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resourceincludes
dev_langs:
- C++
helpviewer_keywords:
- Resource Includes dialog box [C++]
- rc files [C++], changing storage
- symbol header files [C++], changing
- .rc files [C++], changing storage
- symbol header files [C++], read-only
- symbols [C++], symbol header files
ms.assetid: 659a54e6-e416-4045-8411-798730ff4ce3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 626327fec8efda873551e6d9ee502d7405eec5a7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371984"
---
# <a name="resource-includes-dialog-box-c"></a>Inclusión de recursos de cuadro de diálogo) (C++)

Puede usar el **incluye recursos** cuadro de diálogo en un proyecto de C++ para modificar trabajo habitual del entorno de almacenamiento de todos los recursos en el archivo .rc del proyecto y todos [símbolos](../windows/symbols-resource-identifiers.md) en Resource.h.

Para abrir el **incluye recursos** de archivos en el cuadro de diálogo, haga una .rc [vista de recursos](../windows/resource-view-window.md), a continuación, elija **incluye recursos** en el menú contextual.

- **Archivo de encabezado de símbolos**

   Permite cambiar el nombre del archivo de encabezado donde se almacenan las definiciones de los símbolos del archivo de recursos. Para obtener más información, consulte [cambiar los archivos de encabezado de los nombres de símbolos](../windows/changing-the-names-of-symbol-header-files.md).

- **Directivas de símbolos de solo lectura**

   Permite incluir archivos de encabezado cuyos símbolos no deberían modificarse durante una sesión de edición. Por ejemplo, se puede incluir un archivo de símbolos compartido por varios proyectos. También se pueden incluir archivos .h de MFC. Para obtener más información, consulte [símbolos incluidos compartidos (de solo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md).

- **Directivas de tiempo de compilación**

   Permite incluir archivos de recursos creados y editados con independencia de los recursos del archivo principal de recursos, con directivas de tiempo de compilación (como las que incluyen de forma condicional recursos) o con recursos en formato personalizado. También puede usar el **cuadro directivas de tiempo de compilación** para incluir archivos de recursos MFC estándares. Para obtener más información, consulte [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).

> [!NOTE]
> Las entradas de estos cuadros de texto aparecen en el archivo .rc marcadas por `TEXTINCLUDE 1`, `TEXTINCLUDE 2`, y `TEXTINCLUDE 3` respectivamente. Para obtener más información, consulte [TN035: usar varios archivos de recursos y archivos de encabezado con Visual C++](../mfc/tn035-using-multiple-resource-files-and-header-files-with-visual-cpp.md).

Una vez que se ha realizado cambios en el archivo de recursos mediante el **incluye recursos** cuadro de diálogo, deberá cerrar el archivo .rc y vuelva a abrirlo para que los cambios surtan efecto. Para obtener más información, consulte [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para especificar directorios de inclusión para los recursos](../windows/how-to-specify-include-directories-for-resources.md)<br/>
[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)