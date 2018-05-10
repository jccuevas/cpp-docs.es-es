---
title: Obtener acceso a información de versión desde su programa | Documentos de Microsoft
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
ms.openlocfilehash: e8913e0dc33da1de2f240305ff19f5250e38b180
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="accessing-version-information-from-within-your-program"></a>Obtener información de versión desde un programa
### <a name="to-access-version-information-from-within-your-program"></a>Para obtener acceso a la información de versión desde dentro de su programa  
  
1.  Si quiere tener acceso a la información de versión desde su programa, use la función [GetFileVersionInfo](http://msdn.microsoft.com/library/windows/desktop/ms647003.aspx) y la función [VerQueryValue](http://msdn.microsoft.com/library/windows/desktop/ms647464.aspx) .  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de información de versión](../windows/version-information-editor.md)   
 [Información de versión (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)

