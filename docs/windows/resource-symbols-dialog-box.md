---
title: "Cuadro de diálogo símbolos de recursos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.resourcesymbols
dev_langs: C++
helpviewer_keywords:
- New Symbol dialog box
- Resource Symbols dialog box
- Change Symbol dialog box
ms.assetid: 9706cde3-1f48-4fcd-bedb-2b03b455e3c1
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0e21f60fb2ca90e9e4825e93103fa74be3563780
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-symbols-dialog-box"></a>Símbolos de recursos (cuadro de diálogo)
El **símbolos de recursos** cuadro de diálogo permite agregar símbolos de recursos nuevos, cambiar los símbolos que se muestran o saltar a la ubicación en el código fuente en un símbolo está en uso.  
  
 **Name**  
 Muestra el nombre del símbolo. Para obtener más información, consulte [restricciones de nombre de símbolo](../windows/symbol-name-restrictions.md).  
  
 **Valor**  
 Muestra el valor numérico del símbolo. Para obtener más información, consulte [restricciones de valores de símbolo](../windows/symbol-value-restrictions.md).  
  
 **En uso**  
 Si se selecciona, especifica si el símbolo se usa en uno o varios recursos. El o los recursos se enumeran en el cuadro Usado por.  
  
 **Mostrar símbolos de solo lectura**  
 Si se selecciona, muestra los recursos de solo lectura. De forma predeterminada, el cuadro de diálogo Símbolos de recursos solo muestra los recursos modificables en el archivo de script de recursos. Si selecciona esta opción, los recursos modificables aparecen en negrita y, los de solo lectura, en texto sin formato.  
  
 **Utilizado por**  
 Muestra el o los recursos que usan el símbolo seleccionado en la lista de símbolos. Para abrir el editor para un recurso determinado, seleccione el recurso en el **usado por** y haga clic en **Ver uso**. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).  
  
 **Nuevo**  
 Abre el cuadro de diálogo Nuevo símbolo, que permite definir el nombre y, si es necesario, un valor para el nuevo identificador de recurso simbólico. Para obtener más información, consulte [crear nuevos símbolos](../windows/creating-new-symbols.md).  
  
 **Cambio**  
 Abre el cuadro de diálogo Cambiar símbolo, que permite cambiar el nombre o el valor de un símbolo. Si el símbolo es para un control o un recurso en uso, solo se puede cambiar desde el editor de recursos correspondiente. Para obtener más información, consulte [cambiar símbolos sin asignar](../windows/changing-unassigned-symbols.md).  
  
 **Ver uso**  
 Abre el recurso que contiene el símbolo en el editor de recursos correspondiente. Para obtener más información, consulte [abrir el Editor de recursos para un símbolo determinado](../windows/opening-the-resource-editor-for-a-given-symbol.md).  
  

  
## <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Visualización de símbolos de recursos](../windows/viewing-resource-symbols.md)