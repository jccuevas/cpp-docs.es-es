---
title: Hacer que un objeto ATL no se pueden crear | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.objects
dev_langs:
- C++
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 9ee276d86478bb4a7b6c9839378183bfd49533d6
ms.contentlocale: es-es
ms.lasthandoff: 03/31/2017

---
# <a name="making-an-atl-object-noncreatable"></a>Hacer que una no se pueden crear objetos ATL
Puede cambiar los atributos de un objeto COM basado en ATL para que un cliente no puede crear directamente el objeto. En este caso, el objeto se devuelve a través de una llamada al método en otro objeto en lugar de crear directamente.  
  
### <a name="to-make-an-object-noncreatable"></a>Para crear un objeto  
  
1.  Quitar el [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto) para el objeto. Si desea que el objeto sea noncreatable pero el control se registre, reemplace OBJECT_ENTRY_AUTO con [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](object-map-macros.md#object_entry_non_createable_ex_auto).  
  
2.  Agregar el [noncreatable](../../windows/noncreatable.md) atribuir a la coclase en el archivo IDL. Por ejemplo:  
  
 ```  
 [  
    uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851), 
    helpstring("MyObject"), 
    noncreatable]  
    coclass MyObject  
 {  
 [default] interface IMyInterface;  
 }  
 ```  
  
## <a name="see-also"></a>Vea también  
 [Asistente para proyectos ATL](../../atl/reference/atl-project-wizard.md)   
 [Tipos de proyecto de Visual C++](../../ide/visual-cpp-project-types.md)   
 [Crear proyectos de escritorio con asistentes para aplicaciones](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Programar con ATL y el código de tiempo de ejecución de C](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [Aspectos básicos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configuraciones de proyecto ATL predeterminadas](../../atl/reference/default-atl-project-configurations.md)


