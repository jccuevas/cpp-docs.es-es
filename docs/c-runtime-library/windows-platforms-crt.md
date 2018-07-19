---
title: Plataformas Windows (CRT) | Microsoft Docs
ms.custom: ''
ms.date: 02/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- backward compatibility [C++], C run-time libraries
- compatibility [C++], C run-time libraries
- MBCS [C++], Win32 platforms
- operating systems [C++]
- Unicode [C++], Win32 platforms
ms.assetid: 0aacaf45-6dc4-4908-bd52-57abac7b39f6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d53e8020bbb7649d78232025ef9c63c1dc868fee
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409012"
---
# <a name="windows-platforms-crt"></a>Plataformas Windows (CRT)

Las bibliotecas de tiempo de ejecución de C para Visual Studio admiten las versiones actuales de Windows y Windows Server, [!INCLUDE[win8](../build/reference/includes/win8_md.md)], [!INCLUDE[winserver8](../build/reference/includes/winserver8_md.md)], [!INCLUDE[win7](../build/includes/win7_md.md)], [!INCLUDE[winsvr08](../build/reference/includes/winsvr08_md.md)], así como Windows Vista y, opcionalmente [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 3 (SP3) para 86 bits, [!INCLUDE[winxp](../build/includes/winxp_md.md)] Service Pack 2 (SP2) para 64 bits y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)] Service Pack 2 (SP2) tanto para 86 como 64 bits. Todos estos sistemas operativos admiten la API para escritorio de Windows (Win32) y ofrecen compatibilidad con Unicode. Además, cualquier aplicación Win32 puede usar un juego de caracteres multibyte (MBCS).

> [!NOTE]
> La instalación predeterminada de la carga de trabajo de **desarrollo para el escritorio con C++** en Visual Studio 2017 no incluye compatibilidad con el desarrollo para [!INCLUDE[winxp](../build/includes/winxp_md.md)] y [!INCLUDE[WinXPSvr](../build/includes/winxpsvr_md.md)]. Deberá instalar el componente opcional **Compatibilidad de Windows XP con C++** para habilitar un conjunto de herramientas de la plataforma Windows XP.

## <a name="see-also"></a>Vea también

[Compatibilidad](../c-runtime-library/compatibility.md)  
