---
title: Realizar un objeto ATL, no se pueden crear | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
translationtype: Machine Translation
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: b812c2d4bfeb0663d62051c05829f25dc7139faf
ms.lasthandoff: 02/24/2017

---
# <a name="making-an-atl-object-noncreatable"></a>Realizar una no se pueden crear objetos ATL
Puede cambiar los atributos de un objeto COM basado en ATL para que un cliente no puede crear directamente el objeto. En este caso, el objeto se devuelve a través de una llamada al método en otro objeto en lugar de crear directamente.  
  
### <a name="to-make-an-object-noncreatable"></a>Para crear un objeto  
  
1.  Quitar el [OBJECT_ENTRY_AUTO](http://msdn.microsoft.com/library/5a0f4fa5-0905-43d2-b337-e22f979c9e4c) para el objeto. Si desea que el objeto sea noncreatable pero pueda registrar el control, reemplace OBJECT_ENTRY_AUTO con [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](http://msdn.microsoft.com/library/abdc093c-6502-42de-8419-b7ebf45299d1).  
  
2.  Agregue el [noncreatable](../../windows/noncreatable.md) a la coclase en el archivo .idl del atributo. Por ejemplo:  
  
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
 [Fundamentos de los objetos ATL COM](../../atl/fundamentals-of-atl-com-objects.md)   
 [Configuraciones predeterminadas de proyecto ATL](../../atl/reference/default-atl-project-configurations.md)


