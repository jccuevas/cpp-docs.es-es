---
title: / INTEGRITYCHECK | Documentos de Microsoft
ms.custom: 
ms.date: 12/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /INTEGRITYCHECK
dev_langs:
- C++
helpviewer_keywords:
- -INTEGRITYCHECK editbin options
- /INTEGRITYCHECK editbin options
- INTEGRITYCHECK editbin options
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99caec18162a7506b8b7a467eb7374b6fe4a38d9
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/03/2018
---
# <a name="integritycheck"></a>/INTEGRITYCHECK

Especifica que la firma digital de la imagen binaria debe estar activada en tiempo de carga.

> **/ INTEGRITYCHECK**[**: N**]

## <a name="remarks"></a>Comentarios

En el encabezado del archivo DLL o el archivo ejecutable, esta opción establece una marca que requiere una comprobación de firma digital mediante el Administrador de memoria para cargar la imagen de Windows. Las versiones de Windows anteriores a Windows Vista omiten esta marca. Esta opción debe establecerse para archivos DLL de 64 bits que implementan código en modo kernel y se recomienda para todos los controladores de dispositivo. Para obtener más información, consulte [requisitos de firma de código de modo Kernel](/windows-hardware/drivers/install/kernel-mode-code-signing-requirements--windows-vista-and-later-).

## <a name="see-also"></a>Vea también

[Opciones de EDITBIN](../../build/reference/editbin-options.md)  
