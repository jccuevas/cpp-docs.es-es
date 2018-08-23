---
title: 'Cómo: copiar recursos | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f9cef186c18622dc361f97bd65e7bd264a6f03cf
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42599589"
---
# <a name="how-to-copy-resources"></a>Cómo: Copiar recursos

Puede copiar los recursos de un archivo a otro sin cambiarlas o bien puede [cambiar el idioma o la condición de un recurso al copiarlo](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md).

Puede copiar fácilmente recursos desde un recurso existente o un archivo ejecutable para el archivo de recursos actual. Para ello, abra ambos archivos que contienen recursos al mismo tiempo y arrastrar elementos desde un archivo a otro o copiar y pegar entre los dos archivos. Este método funciona para archivos de recursos (.rc) de la secuencia de comandos y archivos de recursos (.rct) de la plantilla, así como archivos ejecutables (.exe).

> [!NOTE]
> Visual C++ incluye archivos de recursos de ejemplo que puede usar en su propia aplicación. Para obtener más información, consulte [CLIPART: recursos comunes](http://msdn.microsoft.com/9bac2891-b6b3-49ec-a287-cec850c707e0).

Puede usar el método de arrastrar y colocar entre archivos .rc que estén abiertos [fuera del proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).

### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>Para copiar recursos entre archivos mediante el método de arrastrar y colocar

1. Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo fuera de un proyecto de .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, abra Source1.rf y Source2.rc.

2. En el primer archivo .rc, haga clic en el recurso que desea copiar. Por ejemplo, en `Source1.rc`, haga clic en **IDD_DIALOG1**.

3. Mantenga presionada la tecla CTRL y arrastre el recurso para el segundo archivo. rc. Por ejemplo, arrastre **IDD_DIALOG1** desde `Source1.rc` a `Source2.rc`.

   > [!NOTE]
   > Arrastrar el recurso sin mantener presionada la **Ctrl** tecla mueve el recurso, en lugar de copiarlo.

### <a name="to-copy-resources-using-copy-and-paste"></a>Para copiar recursos con copiar y pegar

1. Abra ambos archivos de recursos independientes (para obtener más información, consulte [ver recursos en un archivo fuera de un proyecto de .rc](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)). Por ejemplo, Source1.RF y Source2.rc.

2. En el archivo de origen desde el que desea copiar un recurso (por ejemplo, `Source1.rc`), haga clic en un recurso y elija **copia** en el menú contextual.

3. Haga clic en el archivo de recursos en la que desea pegar el recurso (por ejemplo, `Source2.rc`). Elija **pegar** en el menú contextual.

   > [!NOTE]
   > No se puede arrastrar y soltar, copiar, cortar o pegar entre archivos de recursos en el proyecto (**vista de recursos**) y archivos .rc independientes (aquellas abiertos en ventanas de documento). Podría hacerlo en las versiones anteriores del producto.

   > [!NOTE]
   > Para evitar conflictos con los nombres de símbolos o valores en el archivo existente, Visual C++ puede cambiar valor de símbolo del recurso transferido o nombre de símbolo y el valor cuando se copia al nuevo archivo.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para abrir un archivo de script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
[Archivos de recursos](../windows/resource-files-visual-studio.md)  
[Editores de recursos](../windows/resource-editors.md)