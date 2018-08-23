---
title: Editar datos binarios | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- binary data
ms.assetid: 0fd429de-baf1-4871-b5e4-42bf868a3261
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 96a4370d56e2f5d9758e97010965668bd08306c3
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42593010"
---
# <a name="editing-binary-data"></a>Editar datos binarios

### <a name="to-edit-a-resource-in-the-binary-editor"></a>Para editar un recurso en el editor binario

1. Seleccione el byte que se va a editar.

   El **ficha** tecla mueve el foco entre las secciones hexadecimal y ASCII de la **binario** editor. Puede usar el **RE PÁG** y **AV PÁG** teclas para desplazarse por los recursos de la pantalla a la vez.

2. Escriba el nuevo valor.

   El valor cambia inmediatamente en las secciones de ASCII y hexadecimales y foco se desplaza hasta el siguiente valor en línea.

   > [!NOTE]
   > El **binario** editor acepta los cambios automáticamente al cerrar el editor.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Binary Editor](binary-editor.md)