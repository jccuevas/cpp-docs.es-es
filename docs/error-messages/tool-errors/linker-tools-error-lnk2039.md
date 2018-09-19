---
title: Error de las LNK2039 las herramientas del vinculador | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2039
dev_langs:
- C++
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac4fdde90911427a1a193bfb6f3a950a7bdcf180
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081798"
---
# <a name="linker-tools-error-lnk2039"></a>Error de las herramientas del vinculador LNK2039

importación de la clase ref\<tipo >' que se define en another.obj; debe ser importado o definirse, pero no ambos

La clase ref ' <`type`>' se importa en el archivo .obj especificado, pero también se define en otro archivo obj. Esta condición puede provocar un error en tiempo de ejecución u otro comportamiento inesperado.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe si '`type`' debe definirse en el otro archivo .obj y compruebe si se debe importar desde el archivo .winmd.

1. Quite la definición o la importación.

## <a name="see-also"></a>Vea también

[Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Error de las herramientas del vinculador LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)