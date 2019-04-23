---
title: Identificadores de recursos (símbolos) (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: 0b19ff0d1c709616868d47c172ff4cf8c6931b82
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036054"
---
# <a name="resource-identifiers-symbols-c"></a>Identificadores de recursos (símbolos) (C++)

Un símbolo es un identificador de recursos (ID) que consta de dos partes, un nombre de símbolo (cadena de texto) que se asigna a un valor de símbolo (entero), por ejemplo:

```
IDC_EDITNAME = 5100
```

Los nombres de símbolos a menudo se denominan identificadores.

Los símbolos ofrecen un medio descriptivo para hacer referencia a los recursos y objetos de interfaz de usuario, tanto en el código fuente como mientras trabaja con ellos en los editores de recursos. Puede ver y manipular símbolos en un lugar cómodo mediante el [cuadro de diálogo Símbolos de recursos](../windows/viewing-resource-symbols.md).

Conforme aumenta el tamaño y la sofisticación de su aplicación, lo hacen también su número de recursos y símbolos. El seguimiento de grandes números de símbolos dispersos en varios archivos puede resultar difícil. El **símbolos de recursos** cuadro de diálogo simplifica la administración de símbolos mediante una herramienta central que permite:

- [Creación de símbolos](../windows/creating-new-symbols.md)

- [Administrar los símbolos](../windows/changing-a-symbol-or-symbol-name-id.md)

- [Ver id. de de símbolos predefinidos](../windows/predefined-symbol-ids.md)

Cuando crea un nuevo recurso o un objeto de recurso, los [editores de recursos](../windows/resource-editors.md) ofrecen un nombre predeterminado para el recurso, por ejemplo, `IDC_RADIO1`, y le asignan un valor. La definición de nombre y valor se almacena en el `Resource.h` archivo.

> [!NOTE]
> Cuando se copian recursos u objetos de recursos de un archivo .rc a otro, Visual C++ puede cambiar el valor del símbolo del recurso transferido, o el nombre del símbolo y el valor, para evitar conflictos con nombres de símbolos o valores del archivo existente.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)<br/>