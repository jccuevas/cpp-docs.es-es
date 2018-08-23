---
title: 'Cómo: cambiar el idioma o la condición de un recurso al copiarlo | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.changing
dev_langs:
- C++
helpviewer_keywords:
- Language property
- condition property of resource
ms.assetid: 8f622ab0-bac2-468f-ae70-78911afc4759
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 508655dbfeb2d06d936d2b73d5435cf04c860f4b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598939"
---
# <a name="how-to-change-the-language-or-condition-of-a-resource-while-copying"></a>Cómo: Cambiar el idioma o la condición de un recurso al copiarlo

Al copiar un recurso, puede cambiar sus propiedades de idioma, condición o ambas.

- El idioma del recurso identifica exactamente eso, el idioma del recurso. Esto sirve para [FindResource](http://msdn.microsoft.com/library/windows/desktop/ms648042) para ayudar a identificar el recurso que está buscando. (Sin embargo, los recursos pueden tener diferencias para cada idioma que no estén relacionados con texto, por ejemplo, aceleradores que solo funcionen en teclados japoneses, un mapa de bits que solo sea adecuado para compilaciones localizadas en chino, etc.).

- La condición de un recurso es un símbolo definido que identifica una condición en la que esta copia concreta del recurso se va a utilizar.

El idioma y la condición de un recurso se muestran entre paréntesis después del nombre del recurso en la ventana del área de trabajo. En este ejemplo, el recurso denominado IDD_AboutBox tienen finés como idioma y XX33 como condición.

```cpp
IDD_AboutBox (Finnish - XX33)  
```

### <a name="to-copy-an-existing-resource-and-change-its-language-or-condition"></a>Para copiar un recurso existente y cambiar su idioma o su condición

1. En el archivo .rc o en la [vista de recursos](../windows/resource-view-window.md) ventana, haga clic en el recurso que van a copiar.

2. Elija **Insertar copia** en el menú contextual.

3. En el **Insertar copia de recursos** cuadro de diálogo:

   - Para el **lenguaje** cuadro de lista, seleccione el idioma.

   - En el **condición** , escriba la condición.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para copiar recursos](../windows/how-to-copy-resources.md)  
[Archivos de recursos](../windows/resource-files-visual-studio.md)  
[Editores de recursos](../windows/resource-editors.md)