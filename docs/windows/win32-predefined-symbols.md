---
title: Símbolos predefinidos de Win32 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Win32 [C++], predefined symbols
- symbols [C++], Win32 predefined
- Windows API [C++], predefined symbols
ms.assetid: 45c8e193-ee2a-4024-bfc2-34d1ec9c9239
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: cb24c8d0d24351ba09cdc8750cebbe04f7335942
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313213"
---
# <a name="win32-predefined-symbols"></a>Símbolos predefinidos de Win32

Estos símbolos se definen en los archivos de encabezado de Win32, y admiten las acciones y funciones de aplicación de Windows estándar. Estos símbolos se utilizan principalmente con elementos de interfaz de usuario comunes. Cuando se trabaja con controles en los editores de recursos, estos símbolos aparecen en la [ventana propiedades](/visualstudio/ide/reference/properties-window) asociados a los controles comunes. Por ejemplo, si la barra de herramientas debe mostrarse el icono de aplicación, el icono se asociará con el símbolo IDI_SMALL en el **ventana propiedad**.

|||
|-|-|
|IDABORT|Control: Botón de anulación de cuadro de diálogo|
|IDC_STATIC|Control: Texto estático en un cuadro de diálogo|
|IDCANCEL|Control: Botón de cancelación del cuadro de diálogo|
|IDD_ABOUTBOX|Cuadro de diálogo: Producto sobre el cuadro de diálogo|
|IDI_PROJECTNAME|Icono: Icono del proyecto actual|
|IDI_SMALL|Icono: Proyecto pequeño icono actual|
|IDIGNORE|Control: Se utiliza con el botón Omitir en los cuadros de diálogo|
|IDM_ABOUT|Elemento de menú: Se usa con la Ayuda... Acerca de...|
|IDM_EXIT|Elemento de menú: Se utiliza con archivo... Salida...|
|IDNO|Control: no cuadro de diálogo no hay ningún botón|
|IDOK|Control: Botón Aceptar del cuadro de diálogo|
|IDRETRY|Control: Botón de reintento de cuadro de diálogo|
|IDS_APP_TITLE|Cadena: Nombre actual de la aplicación|
|IDYES|Control: Botón Sí cuadro de diálogo|

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)  
[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)