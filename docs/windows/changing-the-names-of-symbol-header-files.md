---
title: Cambiar los nombres de los archivos de encabezado de símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.changing.header
dev_langs:
- C++
helpviewer_keywords:
- resource files, multiple
- Resource Includes dialog box
- symbol header files, changing names
- symbol header files
- header files, changing names
- names [C++], symbol header files
- symbols, symbol header files
- Resource.h
ms.assetid: b948284a-7899-402e-ab12-9f2c8480ca9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2df697df91374b61b72b9093c8cf16e1ac613863
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42605231"
---
# <a name="changing-the-names-of-symbol-header-files"></a>Cambiar los nombres de los archivos de encabezado de símbolos

Normalmente todos los símbolos se guardan las definiciones en `Resource.h`. Sin embargo, puede que necesite cambiar este nombre de archivo de inclusión para, por ejemplo, poder trabajar con más de un archivo de recursos en el mismo directorio.

### <a name="to-change-the-name-of-the-resource-symbol-header-file"></a>Para cambiar el nombre del archivo de encabezado de símbolos de recurso

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija [incluye recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el **archivo de encabezado de símbolos** , escriba el nuevo nombre del archivo de inclusión.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)  
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)