---
title: 'Cómo: abrir un archivo de Script de recursos fuera de un proyecto (independiente) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.resource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- .rc files, viewing resources
- resource script files, viewing resources
ms.assetid: bc350c60-178d-4c5d-9a7e-6576b0c936e4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 70cba5145f64fd88d1d6f1c4a68ac4c0730968cc
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570388"
---
# <a name="how-to-open-a-resource-script-file-outside-of-a-project-standalone"></a>Cómo: Abrir un archivo de script de recursos fuera de un proyecto (independiente)
Puede ver los recursos en un archivo .rc sin tener un proyecto abierto. El archivo .rc se abrirá en una ventana de documento en lugar de abrirse en el [vista de recursos](../windows/resource-view-window.md) ventana (como ocurre cuando el archivo se abre dentro de un proyecto).  
  
> [!NOTE]
>  Esta distinción es importante porque algunos comandos solo están disponibles cuando el archivo se abre de forma independiente (fuera de un proyecto). Por ejemplo, puede guardar solo un archivo en un formato diferente o como un nombre de archivo diferente cuando se abre el archivo fuera de un proyecto (el **Guardar como** comando no está disponible cuando se abre un archivo dentro de un proyecto).  
  
### <a name="to-open-an-rc-file-outside-a-project"></a>Para abrir un archivo .rc fuera de un proyecto  
  
1.  Desde el **archivo** menú, elija **abierto**, a continuación, haga clic en **archivo**.  
  
2.  En el **abrir archivo** diálogo cuadro, vaya al archivo de script de recursos que desea ver, resalte el archivo y haga clic en **abierto**.  
  
    > [!NOTE]
    >  Si abre primero el proyecto (**archivo**, **abrir**, **proyecto**), algunos comandos no estarán disponibles para usted. Abrir un archivo "independiente" significa abrir sin cargar primero el proyecto.  
  
 Para abrir y ver el archivo de recursos en formato de texto, consulte [editar un Script de recursos (.rc) archivo](../windows/how-to-open-a-resource-script-file-in-text-format.md).  
  
### <a name="to-open-multiple-rc-files-outside-a-project"></a>Para abrir varios archivos .rc fuera de un proyecto  
  
1.  Abra ambos archivos de recursos de manera independiente. Por ejemplo, abra Source1.rf y Source2.rc.  
  
    1.  Desde el **archivo** menú, elija **abierto**, a continuación, haga clic en **archivo**.  
  
    2.  En el **abrir archivo** cuadro de diálogo, navegue hasta el primer archivo de script de recursos que desee abrir (Source 1.rc), resalte el archivo y haga clic en **abrir**.  
  
    3.  Repita el paso anterior para abrir el segundo archivo .rc (Source2.rc).  
  
         Los archivos .rc ahora están abiertos en ventanas de documentos independientes.  
  
2.  Cuando los archivos .rc estén abiertos, coloque las ventanas en mosaico para poder verlos simultáneamente:  
  
    -   Desde el **ventana** menú, elija **nuevo grupo de pestañas Horizontal** o **nuevo grupo de pestañas Vertical**.  
  
         \- o -  
  
    -   Haga clic en uno de los archivos .rc y elija **nuevo grupo de pestañas Horizontal** o **nuevo grupo de pestañas Vertical** en el menú contextual.  
  
> [!NOTE]
>  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)