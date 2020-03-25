---
title: Error de las herramientas del vinculador LNK2039
ms.date: 11/04/2016
f1_keywords:
- LNK2039
helpviewer_keywords:
- LNK2039
ms.assetid: eaa296bd-4901-41f6-8410-6d03ee827144
ms.openlocfilehash: 7712747deb865ec62fa007fcd95ad09630d00cea
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194504"
---
# <a name="linker-tools-error-lnk2039"></a>Error de las herramientas del vinculador LNK2039

importando la clase ref '\<tipo > ' que se define en otro. obj; debe importarse o definirse, pero no ambos

La clase ref ' <`type`> ' se importa en el archivo. obj especificado, pero también se define en otro archivo. obj. Esta condición puede producir un error en tiempo de ejecución u otro comportamiento inesperado.

### <a name="to-correct-this-error"></a>Para corregir este error

1. Compruebe si '`type`' debe definirse en el otro archivo. obj y compruebe si se debe importar desde el archivo. winmd.

1. Quite la definición o la importación.

## <a name="see-also"></a>Consulte también

[Errores y advertencias de las herramientas del vinculador](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)<br/>
[Error de las herramientas del vinculador LNK1332](../../error-messages/tool-errors/linker-tools-error-lnk1332.md)
