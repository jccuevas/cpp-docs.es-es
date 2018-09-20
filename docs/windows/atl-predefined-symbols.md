---
title: Símbolos predefinidos de ATL | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 965eb339295b86c223b5081dede8e33dd282b95d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46386605"
---
# <a name="atl-predefined-symbols"></a>Símbolos predefinidos de ATL

Estos símbolos se definen en los archivos de encabezado ATL, pero admiten acciones y funciones de aplicación de Windows estándares. Estos símbolos se utilizan principalmente con cuadros de diálogo. Cuando se trabaja con controles y cuadros de diálogo en el [editor de cuadro de diálogo](../windows/dialog-editor.md), estos símbolos aparecen en la **propiedades** ventana asociada con los controles comunes. Por ejemplo, si el cuadro de diálogo tiene un **cancelar** button, que se asociará con el símbolo IDCANCEL comandos en el [ventana propiedades](/visualstudio/ide/reference/properties-window).

|||
|-|-|
|IDABORT|Control: Botón de anulación de cuadro de diálogo|
|IDC_STATIC|Control: Control estático|
|IDCANCEL|Control: Botón de cancelación del cuadro de diálogo|
|IDIGNORE|Control: Botón de omitir del cuadro de diálogo|
|IDNO|Control: no cuadro de diálogo no hay ningún botón|
|IDOK|Control: Botón Aceptar del cuadro de diálogo|
|IDR_ACCELERATOR1|Recursos: Tabla de aceleradores|
|IDRETRY|Control: Botón de reintento de cuadro de diálogo|
|IDS_PROJNAME|Cadena: Nombre actual de la aplicación|
|IDYES|Control: Botón Sí cuadro de diálogo|

## <a name="requirements"></a>Requisitos

ATL

## <a name="see-also"></a>Vea también

[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>
[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)