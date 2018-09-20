---
title: Obtener acceso a información de versión desde el programa (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 18622333-d9e8-4309-9465-677cd10c79b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ac344242a55ba9d2f3c6ec2846feb18f70bf6483
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46421523"
---
# <a name="accessing-version-information-from-within-your-program-c"></a>Obtener acceso a información de versión desde el programa (C++)

### <a name="to-access-version-information-from-within-your-program"></a>Para obtener acceso a la información de versión desde dentro de su programa

1. Si desea tener acceso a la información de versión desde su programa, use la [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) función y el [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) función.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de la información de versión](../windows/version-information-editor.md)<br/>
[Información de versión (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)