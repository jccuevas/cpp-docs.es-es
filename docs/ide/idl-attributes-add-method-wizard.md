---
title: Atributos IDL, Asistente para agregar métodos | Microsoft Docs
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
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33337774"
---
# <a name="idl-attributes-add-method-wizard"></a>Atributos IDL, Asistente para agregar métodos
Use esta página del Asistente para agregar métodos para especificar la configuración de lenguaje de definición de interfaz (IDL) para el método.  
  
 **identificador**  
 Establece el id. numérico que identifica el método. Vea [id](http://msdn.microsoft.com/library/windows/desktop/aa367040) en la *Referencia de MIDL*.  
  
 Este cuadro no está disponible para las interfaces personalizadas y tampoco para las interfaces dispinterface de MFC.  
  
 **call_as**  
 Especifica el nombre de un método remoto al que se puede asignar este método local. Vea [call_as](http://msdn.microsoft.com/library/windows/desktop/aa366748) en la *Referencia de MIDL*.  
  
 No está disponible para interfaces dispinterface de MFC.  
  
 **helpcontext**  
 Especifica un id. contextual que permite al usuario ver información sobre este método en el archivo de ayuda. Vea [helpcontext](http://msdn.microsoft.com/library/windows/desktop/aa366851) en la *Referencia de MIDL*.  
  
 No está disponible para interfaces dispinterface de MFC.  
  
 **helpstring**  
 Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica. De forma predeterminada, se establece en "method *nombre del método*". Vea [helpstring](http://msdn.microsoft.com/library/windows/desktop/aa366856) en la *Referencia de MIDL*.  
  
 No está disponible para interfaces dispinterface de MFC.  
  
 **Atributos adicionales**  
 No está disponible para interfaces dispinterface de MFC.  
  
|Atributo|Description|  
|---------------|-----------------|  
|**hidden**|Indica que el método existe pero que no se debe mostrar en un explorador orientado al usuario. Vea [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) en la *Referencia de MIDL*.|  
|**source**|Indica que un miembro del método es un origen de eventos. Vea [source](http://msdn.microsoft.com/library/windows/desktop/aa367166) en la *Referencia de MIDL*.|  
|`local`|Especifica al compilador MIDL que el método no es remoto. Vea [local](http://msdn.microsoft.com/library/windows/desktop/aa367071) en la *Referencia de MIDL*.|  
|**restricted**|Especifica que no se puede llamar a este método de manera arbitraria. Vea [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) en la *Referencia de MIDL*.|  
|**vararg**|Especifica que el método toma un número variable de argumentos. Para conseguirlo, el último argumento debe ser una matriz segura de tipo **VARIANT** que contenga todos los argumentos restantes. Vea [vararg](http://msdn.microsoft.com/library/windows/desktop/aa367304) en la *Referencia de MIDL*.|  
  
## <a name="see-also"></a>Vea también  
 [Agregar un método](../ide/adding-a-method-visual-cpp.md)   
 [Asistente para agregar métodos](../ide/add-method-wizard.md)