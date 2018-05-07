---
title: Atributos IDL, Asistente para agregar métodos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.method.idlattrib
dev_langs:
- C++
helpviewer_keywords:
- Add Method Wizard [C++]
- IDL attributes, Add Method Wizard
ms.assetid: f80c3bc1-b515-4d6c-83ee-98c2c21ba902
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4a7a1e8fe89f64ad5909e7c1415545e3b3d80196
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="idl-attributes-add-method-wizard"></a>Atributos IDL, Asistente para agregar métodos
Utilice esta página del Asistente para agregar método para especificar la configuración de idioma (IDL) de definición de interfaz para el método.  
  
 **identificador**  
 Establece el identificador numérico que identifica el método. Vea [identificador](http://msdn.microsoft.com/library/windows/desktop/aa367040) en el *MIDL referencia*.  
  
 Este cuadro no está disponible para las interfaces personalizadas y no está disponible para interfaces dispinterface MFC.  
  
 **call_as**  
 Especifica el nombre de un método remoto al que se puede asignar este método local. Vea [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) en el *MIDL referencia*.  
  
 No está disponible para interfaces dispinterface MFC.  
  
 **helpcontext**  
 Especifica un identificador de contexto que permite al usuario ver información acerca de este método en el archivo de ayuda. Vea [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) en el *MIDL referencia*.  
  
 No está disponible para interfaces dispinterface MFC.  
  
 **helpstring**  
 Especifica una cadena de caracteres que se utiliza para describir el elemento al que se aplica. De forma predeterminada, se establece en "método *nombre del método*." Vea [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) en el *MIDL referencia*.  
  
 No está disponible para interfaces dispinterface MFC.  
  
 **Atributos adicionales**  
 No está disponible para interfaces dispinterface MFC.  
  
|Atributo|Descripción|  
|---------------|-----------------|  
|**hidden**|Indica que el método existe pero no se debe mostrar en un explorador orientado al usuario. Vea [oculto](http://msdn.microsoft.com/library/windows/desktop/aa366861) en el *MIDL referencia*.|  
|**Origen**|Indica que un miembro del método es un origen de eventos. Vea [origen](http://msdn.microsoft.com/library/windows/desktop/aa367166) en el *MIDL referencia*.|  
|`local`|Especifica que el compilador MIDL que el método no es remoto. Vea [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) en el *MIDL referencia*.|  
|**restricted**|Especifica que el método no se puede llamar arbitrariamente. Vea [restringido](http://msdn.microsoft.com/library/windows/desktop/aa367157) en el *MIDL referencia*.|  
|**vararg**|Especifica que el método toma un número variable de argumentos. Para lograr esto, el último argumento debe ser una matriz segura de **VARIANT** tipo que contiene todos los argumentos restantes. Vea [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) en el *MIDL referencia*.|  
  
## <a name="see-also"></a>Vea también  
 [Agregar un método](../ide/adding-a-method-visual-cpp.md)   
 [Asistente para agregar métodos](../ide/add-method-wizard.md)