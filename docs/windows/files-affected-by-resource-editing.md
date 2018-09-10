---
title: Archivos afectados por los recursos de edición (C++) | Microsoft Docs
ms.custom: ''
ms.date: 06/18/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- resource editing
- resources [C++], editing
ms.assetid: d0820df1-ba84-40ac-bce9-29ea5ee7e3f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7b70a24e77e581ebab792d9fca4d7d1a3bd8db12
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316281"
---
# <a name="files-affected-by-resource-editing-c"></a>Archivos afectados por los recursos de edición (C++)

Durante la sesión de edición de recursos, el entorno de Visual Studio funciona con los archivos que se muestran en la tabla siguiente.

|Nombre de archivo|Descripción|
|---------------|-----------------|
|Resource.h|Archivo de encabezado generado por el entorno de desarrollo; contiene las definiciones de símbolos. (Incluye este archivo en el control de código fuente).|
|Filename.aps|Versión binaria del archivo actual de script de recursos; se utiliza para acelerar la carga.<br /><br /> Los editores de recursos no leen directamente los archivos .rc o resource.h. El compilador de recursos los compila en archivos .aps, que son los que usan los editores de recursos. Este archivo es un paso de compilación y solamente almacena datos simbólicos. Como en un proceso de compilación normal, la información que no es simbólica (por ejemplo, los comentarios) se descarta durante el proceso de compilación. Siempre que el archivo .aps se desincroniza con el archivo .rc, este se vuelve a generar (por ejemplo, al guardar, el editor de recursos sobrescribe los archivos .rc y resource.h). Los cambios realizados en los propios recursos permanecerán en el archivo .rc, pero siempre se perderán los comentarios cuando se sobrescriba el archivo .rc. Para obtener información sobre cómo conservar los comentarios, vea [incluir recursos en tiempo de compilación](../windows/how-to-include-resources-at-compile-time.md). (Normalmente, no se debe incluir el archivo .aps en control de código fuente.)|
|.rc|Archivo de script de recursos que contiene script para los recursos del proyecto actual. Este archivo se sobrescribe con el archivo .aps cada vez que se guarda. (Incluye este archivo en el control de código fuente).|

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)