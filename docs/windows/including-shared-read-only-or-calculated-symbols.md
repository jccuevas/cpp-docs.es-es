---
title: Incluidos comparten (de sólo lectura) o calculados símbolos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.shared.calculated
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], read-only
- symbols [C++], shared
- symbols [C++], calculated
- read-only symbols
- symbol directives
- calculated symbols
- shared symbols
ms.assetid: 32b77faf-a066-4371-a072-9a5b84c0766d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 329f1d21489b57130531db20014e249588f101a6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46400515"
---
# <a name="including-shared-read-only-or-calculated-symbols"></a>Incluir símbolos compartidos (de sólo lectura) o calculados

La primera vez que el entorno de desarrollo lee un archivo de recursos creado por otra aplicación, marca todos los archivos de encabezado incluidos como de solo lectura. Posteriormente, puede usar el [incluye recursos de cuadro de diálogo](../windows/resource-includes-dialog-box.md) para agregar archivos de encabezado de símbolos de solo lectura adicionales.

Tal vez le interese usar definiciones de símbolos de solo lectura para los archivos de símbolos que desea compartir entre varios proyectos.

También puede usar los archivos de símbolos incluidos cuando dispone de recursos existentes con definiciones de símbolos que usan expresiones en lugar de enteros sencillos para definir el valor de símbolo. Por ejemplo:

```cpp
#define   IDC_CONTROL1 2100
#define   IDC_CONTROL2 (IDC_CONTROL1+1)  
```

El entorno interpreta correctamente estos símbolos calculados siempre y cuando:

- Los símbolos calculados se coloquen en un archivo de símbolos de solo lectura.

- El archivo de recursos contenga recursos a los que ya están asignados estos símbolos calculados.

- Se espere una expresión numérica.

> [!NOTE]
> Si se espera una cadena o una expresión numérica, la expresión no se evalúa.

### <a name="to-include-shared-read-only-symbols-in-your-resource-file"></a>Para incluir símbolos compartidos (de solo lectura) en el archivo de recursos

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el archivo .rc y elija [incluye recursos](../windows/resource-includes-dialog-box.md) en el menú contextual.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el **directivas de símbolos de solo lectura** cuadro, use el `#include` directiva de compilador para especificar el archivo donde desea que se conserven los símbolos de solo lectura.

   No llame a los archivos `Resource.h`, ya que es el nombre de archivo usada normalmente en el archivo de encabezado de símbolos principal.

   > [!NOTE]
   > **Importante** lo que escribe en el cuadro directivas de símbolos de solo lectura se incluye en el archivo de recursos exactamente como se escribe. Asegúrese de que lo que escribe no contiene errores de sintaxis o de ortografía.

   Use la **directivas de símbolos de solo lectura** casilla para incluir los archivos con las definiciones de símbolos. No incluya definiciones de recursos; en caso contrario, se crearán definiciones de recursos duplicadas cuando se guarde el archivo.

3. Coloque los símbolos en el archivo especificado.

   Los símbolos de los archivos incluidos de esta manera se evalúan cada vez que abra el archivo de recursos, pero no se reemplazan en el disco cuando guarde el archivo.

4. Haga clic en **Aceptar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Restricciones de los nombres de símbolo](../windows/symbol-name-restrictions.md)<br/>
[Restricciones de los valores de símbolo](../windows/symbol-value-restrictions.md)<br/>
[Identificadores de símbolo predefinidos](../windows/predefined-symbol-ids.md)<br/>
[Símbolos: Identificadores de recursos](../windows/symbols-resource-identifiers.md)