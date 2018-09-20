---
title: 'Símbolos: Identificadores de recursos (C++) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.identifiers
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3bbcc774115311cd4ed0f302e4d9812ecfc6505
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422276"
---
# <a name="symbols-resource-identifiers-c"></a>Símbolos: Identificadores de recursos (C++)

Un símbolo es un identificador de recurso (id.) que consta de dos partes: una cadena de texto (nombre del símbolo) asignada a un valor entero (valor del símbolo). Por ejemplo:

```
IDC_EDITNAME = 5100
```

Los nombres de símbolos a menudo se denominan identificadores.

Los símbolos ofrecen un medio descriptivo para hacer referencia a los recursos y objetos de interfaz de usuario, tanto en el código fuente como mientras trabaja con ellos en los editores de recursos. Puede ver y manipular símbolos en un lugar cómodo mediante el [cuadro de diálogo Símbolos de recursos](../windows/viewing-resource-symbols.md).

Cuando crea un nuevo recurso o un objeto de recurso, los [editores de recursos](../windows/resource-editors.md) ofrecen un nombre predeterminado para el recurso, por ejemplo, `IDC_RADIO1`, y le asignan un valor. La definición de nombre y valor se almacena en el archivo Resource.h.

> [!NOTE]
> Cuando se copian recursos u objetos de recursos de un archivo .rc a otro, Visual C++ puede cambiar el valor del símbolo del recurso transferido, o el nombre del símbolo y el valor, para evitar conflictos con nombres de símbolos o valores del archivo existente.

Conforme aumenta el tamaño y la sofisticación de su aplicación, lo hacen también su número de recursos y símbolos. El seguimiento de grandes números de símbolos dispersos en varios archivos puede resultar difícil. El [cuadro de diálogo Símbolos de recursos](../windows/resource-symbols-dialog-box.md) simplifica la administración de símbolos mediante una herramienta central que permite:

- [Ver símbolos de recursos](../windows/viewing-resource-symbols.md)

- [Crear nuevos símbolos](../windows/creating-new-symbols.md)

- [Cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md)

- [Eliminar símbolos sin asignar](../windows/deleting-unassigned-symbols.md)

- [Abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md)

- [Cambiar un símbolo o el nombre de un símbolo (id.)](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Cambiar el valor numérico de un símbolo](../windows/changing-a-symbol-s-numeric-value.md)

- [Cambiar los nombres de los archivos de encabezado de símbolos](../windows/changing-the-names-of-symbol-header-files.md)

- [Incluir símbolos compartidos (de sólo lectura) o calculados](../windows/including-shared-read-only-or-calculated-symbols.md)

- [Ver id. de de símbolos predefinidos](../windows/predefined-symbol-ids.md)

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para buscar símbolos en recursos](../windows/how-to-search-for-symbols-in-resources.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)