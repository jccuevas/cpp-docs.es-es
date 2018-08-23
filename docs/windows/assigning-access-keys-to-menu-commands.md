---
title: Asignar teclas de acceso a comandos de menú | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- access keys [C++], checking
- menus, shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics, adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics, uniqueness checking
- Check Mnemonics command
ms.assetid: fbcf1a00-af6a-4171-805a-0ac01d4e8b0d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ab8ebb204b30883894e04c5d5d8a90f12c63a29b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42591473"
---
# <a name="assigning-access-keys-to-menu-commands"></a>Asignar teclas de acceso a comandos de menú

Puede asignar una tecla de acceso, que permite al usuario seleccionar el menú con el teclado, para los menús y comandos de menú.

### <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Para asignar una tecla de acceso (método abreviado) a un comando de menú

1. Escriba una y comercial (`&`) delante de una letra en el nombre de menú o el nombre de comando para especificar esa letra como tecla de acceso correspondiente. Por ejemplo "& archivo" define **Alt**+**F** como tecla de método abreviado para el **archivo** menú en aplicaciones escritas para Microsoft Windows.

   El elemento de menú ofrecerá una indicación visible de que una de las letras tiene asignada una tecla de método abreviado. La letra que sigue a la y comercial aparece subrayada (depende del sistema operativo).

   > [!NOTE]
   > Para asegurarse de que todas las teclas de acceso de un menú son únicas, haga clic con el botón secundario en el menú y elija **Comprobar teclas de acceso** en el menú contextual.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de menús](../windows/menu-editor.md)