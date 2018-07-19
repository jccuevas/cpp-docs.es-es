---
title: 'Cómo: crear un archivo de Script de recursos | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- rc files, creating
- .rc files, creating
- resource script files, creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a15352640a39ff6adc3b5a956a1f32c9fd414272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875528"
---
# <a name="how-to-create-a-resource-script-file"></a>Cómo: Crear un nuevo archivo de script de recursos
> [!NOTE]
>  El Editor de recursos no está disponible en las ediciones Express.  
>   
>  Este material se aplica a aplicaciones de escritorio de Windows. Los proyectos en lenguajes .NET no utilizan archivos de script de recursos. Para obtener más información, vea [Archivos de recursos](../windows/resource-files-visual-studio.md).  
  
### <a name="to-create-a-new-resource-script-rc-file"></a>Para crear un nuevo archivo de script de recursos (.rc)  
  
1.  Sitúe el foco en la carpeta del proyecto existente en `Solution Explorer`; por ejemplo, "MyProject".  
  
    > [!NOTE]
    >  No confunda la carpeta del proyecto con la carpeta de soluciones del Explorador de soluciones. Si coloca el foco en la carpeta de soluciones, las opciones del cuadro de diálogo **Agregar nuevo elemento** (en el paso 3) serán diferentes.  
  
2.  En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.  
  
3.  En el cuadro de diálogo **Agregar nuevo elemento** , haga clic en la carpeta **Visual C++** y elija **Archivo de recursos (.rc)** en el panel de la derecha.  
  
4.  Asigne un nombre al archivo de script de recursos en el cuadro de texto **Nombre** y después haga clic en **Abrir**.  
  
 A partir de ese momento, podrá [crear](../windows/how-to-create-a-resource.md) y agregar recursos al archivo .rc.  
  
> [!NOTE]
>  Solo se puede agregar un script de recursos (archivo .rc) a un proyecto existente que esté cargado en el IDE de Visual Studio. No es posible crear archivos .rc independientes (fuera de un proyecto). [Las plantillas de recursos](../windows/how-to-use-resource-templates.md) (archivos .rct) pueden crearse en cualquier momento.  
  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)