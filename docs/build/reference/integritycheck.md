---
title: /INTEGRITYCHECK
ms.date: 12/28/2017
f1_keywords:
- /INTEGRITYCHECK
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
ms.openlocfilehash: 4174e22dcdadb3b3319998614285c13741fe3a88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269770"
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.

> **/INTEGRITYCHECK**[**:NO**]

## <a name="remarks"></a>Comentarios

En el encabezado del archivo DLL o el archivo ejecutable, esta opción establece una marca que requiere una comprobación de firma digital mediante el Administrador de memoria para cargar la imagen de Windows. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Esta opción debe establecerse para archivos DLL de 64 bits que implementan código en modo kernel y se recomienda para todos los controladores de dispositivo. Para obtener más información, consulte [requisitos de firma de código de modo Kernel](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](editbin-options.md)
