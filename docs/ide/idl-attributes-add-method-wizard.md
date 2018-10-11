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
ms.openlocfilehash: ce9042a980190bf1fe3da06fb4a9843f73294dee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398851"
---
# <a name="idl-attributes-add-method-wizard"></a>Atributos IDL, Asistente para agregar métodos

Use esta página del Asistente para agregar métodos para especificar la configuración de lenguaje de definición de interfaz (IDL) para el método.

- **identificador**

   Establece el id. numérico que identifica el método. Vea [id](/windows/desktop/Midl/id) en la *Referencia de MIDL*.

   Este cuadro no está disponible para las interfaces personalizadas y tampoco para las interfaces dispinterface de MFC.

- **call_as**

   Especifica el nombre de un método remoto al que se puede asignar este método local. Vea [call_as](/windows/desktop/Midl/call-as) en la *Referencia de MIDL*.

   No está disponible para interfaces dispinterface de MFC.

- **helpcontext**

   Especifica un id. contextual que permite al usuario ver información sobre este método en el archivo de ayuda. Vea [helpcontext](/windows/desktop/Midl/helpcontext) en la *Referencia de MIDL*.

   No está disponible para interfaces dispinterface de MFC.

- **helpstring**

   Especifica una cadena de caracteres que se usa para describir el elemento al que se aplica. De forma predeterminada, se establece en "method *nombre del método*". Vea [helpstring](/windows/desktop/Midl/helpstring) en la *Referencia de MIDL*.

   No está disponible para interfaces dispinterface de MFC.

- **Atributos adicionales**

   No está disponible para interfaces dispinterface de MFC.

   |Atributo|Descripción|
   |---------------|-----------------|
   |**hidden**|Indica que el método existe pero que no se debe mostrar en un explorador orientado al usuario. Vea [hidden](/windows/desktop/Midl/hidden) en la *Referencia de MIDL*.|
   |**source**|Indica que un miembro del método es un origen de eventos. Vea [source](/windows/desktop/Midl/source) en la *Referencia de MIDL*.|
   |`local`|Especifica al compilador MIDL que el método no es remoto. Vea [local](/windows/desktop/Midl/local) en la *Referencia de MIDL*.|
   |**restricted**|Especifica que no se puede llamar a este método de manera arbitraria. Vea [restricted](/windows/desktop/Midl/restricted) en la *Referencia de MIDL*.|
   |**vararg**|Especifica que el método toma un número variable de argumentos. Para conseguirlo, el último argumento debe ser una matriz segura de tipo **VARIANT** que contenga todos los argumentos restantes. Vea [vararg](/windows/desktop/Midl/vararg) en la *Referencia de MIDL*.|

## <a name="see-also"></a>Vea también

[Agregar un método](../ide/adding-a-method-visual-cpp.md)<br>
[Asistente para agregar métodos](../ide/add-method-wizard.md)