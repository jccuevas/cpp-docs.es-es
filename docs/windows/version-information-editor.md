---
title: Editor de información de versión | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version.F1
dev_langs:
- C++
helpviewer_keywords:
- Version Information editor, about Version Information editor
- editors, Version Information
- resource editors, Version Information editor
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 76a76dbb3d8b41c2366f354f9c3c8d66ccc3743f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33890595"
---
# <a name="version-information-editor"></a>Editor de la información de versión
La información de versión consta de la identificación del producto y la empresa, un número de versión del producto, y la notificación de copyright y marca comercial. Con el editor de Información de versión, crea y mantiene estos datos, que se almacenan en el recurso de información de versión. Una aplicación no requiere el recurso de información de versión, pero es un lugar útil para recopilar información que identifica la aplicación. También se usa la información de versión por las API de instalación.  
  
 Un recurso de información de versión tiene un bloque superior y uno o más bloques inferiores: un único bloque de información fija en la parte superior y uno o más bloques de información de versión en la parte inferior (para otros idiomas o juegos de caracteres). El bloque superior tiene tanto cuadros numéricos editables como listas desplegables seleccionables. Los bloques inferiores solo tienen cuadros de texto editables.  
  
> [!NOTE]
>  El estándar de Windows es tener únicamente un recurso de versión, llamado VS_VERSION_INFO.  
  
 El editor de información de versión le permite:  
  
-   [Editar una cadena en un recurso de información de versión.](../windows/editing-a-string-in-a-version-information-resource.md)  
  
-   [Agregar información de versión para otro idioma (nuevo bloque de información de versión).](../windows/adding-version-information-for-another-language.md)  
  
-   [Eliminar un bloque de información de versión.](../windows/deleting-a-version-information-block.md)  
  
-   [Obtener acceso a la información de versión desde dentro de su programa.](../windows/accessing-version-information-from-within-your-program.md)  
  
    > [!NOTE]
    >  Al usar el editor de información de versión, en muchos casos puede hacer clic con el botón secundario para mostrar un menú contextual de comandos específicos de recursos. Por ejemplo, si hace clic mientras señala a una entrada de encabezado de bloque, en el menú contextual se muestra los comandos de nueva información del bloque de versión y eliminar información de bloque de versión.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editores de recursos](../windows/resource-editors.md)   
 [Menús y otros recursos](http://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)

