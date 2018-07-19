---
title: Agregar cuadro de diálogo recurso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.insertresource
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], adding
- Add Resource dialog box
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c420a1d72aa4ceca7d71840fcccb451b6e0aba0f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857524"
---
# <a name="add-resource-dialog-box"></a>Agregar recurso (cuadro de diálogo)
Use este cuadro de diálogo para agregar recursos a un proyecto de aplicación de escritorio de Windows de C++.  
  
> [!NOTE]
>  Esta información no se aplica a los recursos en aplicaciones de la plataforma Universal de Windows. Para más información, consulte [recursos de la aplicación y el sistema de administración de recursos](/windows/uwp/app-resources/).  
  
 **Tipo de recurso**  
 Especifica el tipo de recurso que se desea crear.  
  
 Se pueden expandir las categorías de recursos de cursor y de cuadro de diálogo para mostrar otros recursos. Estos recursos se encuentran en ...\Microsoft Visual Studio `version`\VC\VCResourceTemplates\\< LCID\>\mfc.rct. Si agregan archivos .rct, se deben colocar en este directorio o se debe especificar un [incluyen la ruta de acceso](../windows/how-to-specify-include-directories-for-resources.md) para ellos. Los recursos de esos archivos aparecen en el segundo nivel de la categoría correspondiente. No hay ningún límite preestablecido respecto al número de archivos .rct que se pueden agregar.  
  
 Los recursos que se muestran en el nivel superior del control de árbol son los recursos predeterminados suministrados por Visual Studio.  
  
 **Nuevo**  
 Crea un recurso basado en el tipo que ha seleccionado en el **tipo de recurso** cuadro. El recurso se abrirá en el editor correspondiente. Por ejemplo, si crea un recurso de cuadro de diálogo, se abre en el [editor de cuadro de diálogo](../windows/dialog-editor.md).  
  
 **Import**  
 Se abre la **importar** cuadro de diálogo en el que es posible navegar a un recurso que desea importar al proyecto actual. Se puede importar mapas de bits, iconos, cursores, archivos de recursos HTML, archivos de recursos de sonido (.WAV) o archivos de recursos personalizados.  
  
 **Custom**  
 Se abre la [cuadro de diálogo nuevo recurso personalizado](../windows/new-custom-resource-dialog-box.md) en el que puede crear un recurso personalizado. Los recursos personalizados solo se pueden editar en el Editor binario.  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Procedimiento para crear un recurso](../windows/how-to-create-a-resource.md)