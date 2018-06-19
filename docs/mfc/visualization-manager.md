---
title: Administrador de visualización | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Visualization Manager
ms.assetid: c9dd1365-27ac-42e5-8caa-1004525b4129
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 40d16e1373d347b4a715cd6f073211796913bd21
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33384220"
---
# <a name="visualization-manager"></a>Administrador de visualización
El administrador visual es un objeto que controla el aspecto de toda la aplicación. Actúa como una sola clase donde se puede incluir todo el código de dibujo de la aplicación. La biblioteca de MFC incluye varios administradores visuales. También puede crear su propio administrador visual si desea crear una vista personalizada de la aplicación. Las siguientes imágenes muestran la misma aplicación cuando se habilitan diferentes administradores visuales:  
  
 ![MyApp tal y como se presenta CMFCVisualManagerWindows](../mfc/media/vmwindows.png "vmwindows")  
MyApp que utiliza el administrador visual CMFCVisualManagerWindows  
  
 ![MyApp tal y como se presenta CMFCVisualManagerVS2005](../mfc/media/vmvs2005.png "vmvs2005")  
MyApp que utiliza el administrador visual CMFCVisualManagerVS2005  
  
 ![MyApp tal y como se presenta CMFCVisualManagerOfficeXP](../mfc/media/vmofficexp.png "vmofficexp")  
MyApp que utiliza el administrador visual CMFCVisualManagerOfficeXP  
  
 ![MyApp tal y como se presenta CMFCVisualManagerOffice2003](../mfc/media/vmoffice2003.png "vmoffice2003")  
MyApp que utiliza el administrador visual CMFCVisualManagerOffice2003  
  
 ![MyApp tal y como se presenta CMFCVisualManagerOffice2007](../mfc/media/msoffice2007.png "msoffice2007")  
MyApp que utiliza el administrador visual CMFCVisualManagerOffice2007  
  
 De forma predeterminada, el administrador visual mantiene el código de dibujo de varios elementos de interfaz gráfica de usuario. Para proporcionar los elementos de interfaz de usuario personalizados, debe invalidar los métodos de dibujo relacionados del Administrador de visual. Para obtener la lista de estos métodos, consulte [CMFCVisualManager clase](../mfc/reference/cmfcvisualmanager-class.md). Los métodos que se pueden invalidar para proporcionar una apariencia personalizada son todos los métodos que empiezan por `OnDraw`.  
  
 La aplicación puede tener solo una `CMFCVisualManager` objeto. Para obtener un puntero al administrador visual de la aplicación, llame a la función estática [CMFCVisualManager::GetInstance](../mfc/reference/cmfcvisualmanager-class.md#getinstance). Dado que todos los administradores visuales heredan de `CMFCVisualManager`, el `CMFCVisualManager::GetInstance` método obtener un puntero al administrador visual adecuado, incluso si crea un administrador visual personalizado.  
  
 Si desea crear un administrador visual personalizado, debe derivar de un administrador visual que ya existe. Es la clase predeterminada para derivar desde `CMFCVisualManager`. Sin embargo, puede usar un administrador visual diferente si lo mejor es similar a lo que desea para la aplicación. Por ejemplo, si desea utilizar el `CMFCVisualManagerOffice2007` Administrador visual, pero desea sólo cambiar el aspecto de los separadores, se podría derivar la clase personalizada de `CMFCVisualManagerOffice2007`. En este escenario, debe sobrescribir únicamente los métodos para dibujar los separadores.  
  
 Hay dos posibles maneras de utilizar un administrador visual específico para su aplicación. Es una manera de llamar a la [CMFCVisualManager::SetDefaultManager](../mfc/reference/cmfcvisualmanager-class.md#setdefaultmanager) método y pase el administrador visual adecuado como parámetro. En el ejemplo de código siguiente se muestra cómo utilizar la `CMFCVisualManagerVS2005` Administrador visual con este método:  
  
```  
CMFCVisualManager::SetDefaultManager (RUNTIME_CLASS (CMFCVisualManagerVS2005));
```  
  
 La otra forma de utilizar un administrador visual de la aplicación es crearlo manualmente. La aplicación utilizará este nuevo administrador visual para toda la representación. Sin embargo, dado que puede haber solo un `CMFCVisualManager` objeto por aplicación, tendrá que eliminar el administrador visual actual antes de crear uno nuevo. En el ejemplo siguiente, `CMyVisualManager` es un administrador visual personalizado que se deriva de `CMFCVisualManager`. El método siguiente, cambiará el administrador visual se utiliza para mostrar la aplicación, según un índice:  
  
```  
void CMyApp::SetSkin (int index)  
{  
    if (CMFCVisualManager::GetInstance() != NULL)  
 {  
    delete CMFCVisualManager::GetInstance();

 }  
 
    switch (index)  
 {  
    case DEFAULT_STYLE: *// The following statement creates a new CMFCVisualManager  
    CMFCVisualManager::GetInstance();
break;  
 
    case CUSTOM_STYLE:  
    new CMyVisualManager;  
    break; 
 
    default: 
    CMFCVisualManager::GetInstance();
break;  
 }  
 
    CMFCVisualManager::GetInstance()->RedrawAll();

} 
```  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)   
 [CMFCVisualManager (clase)](../mfc/reference/cmfcvisualmanager-class.md)
