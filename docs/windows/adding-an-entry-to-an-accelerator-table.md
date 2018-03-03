---
title: Agregar una entrada a una tabla de aceleradores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- accelerator tables [C++], adding entries
- New Accelerator command
ms.assetid: 559c2415-8323-4339-9447-6966665f8288
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9fe2df81aae0b9b7232443de1db091a9cbb0c0d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-entry-to-an-accelerator-table"></a>Agregar una entrada a una tabla de aceleradores
### <a name="to-add-an-entry-to-an-accelerator-table"></a>Para agregar una entrada a una tabla de aceleradores  
  
1.  Abra la tabla de aceleradores haciendo doble clic en su icono en [vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Doble clic en la tabla de aceleradores y elija **nuevo acelerador** en el menú contextual, o haga clic en la entrada de fila vacía en la parte inferior de la tabla.  
  
3.  Seleccione un [Id. de](id-property.md) en la lista desplegable en el Id. de cuadro o escriba un nuevo identificador en el **Id. de** cuadro.  
  
4.  Tipo de la [clave](../windows/accelerator-key-property.md) que desea usar como acelerador o menú contextual y elija **tecla siguiente** en el menú contextual para establecer una combinación de teclas (el **tecla siguiente** comando es También está disponible desde el **editar** menú).  
  
5.  Cambiar el [modificador](../windows/accelerator-modifier-property.md) y [tipo](../windows/accelerator-type-property.md), si es necesario.  
  
6.  Presione **ENTRAR**.  
  
    > [!NOTE]
    >  Asegúrese de que todos los aceleradores que defina sean únicos. Puede asignar varias combinaciones de teclas al mismo identificador sin que se produzcan efectos negativos; por ejemplo, CTRL+P y F8 pueden asignarse a ID_PRINT. Sin embargo, tener una combinación de teclas asignada a más de un identificador no funcionará bien; por ejemplo, CTRL+Z asignado tanto a ID_SPELL_CHECK como a ID_THESAURUS.  
  

  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editar tablas de aceleradores](../windows/editing-accelerator-tables.md)   
 [Editor de aceleradores](../windows/accelerator-editor.md)