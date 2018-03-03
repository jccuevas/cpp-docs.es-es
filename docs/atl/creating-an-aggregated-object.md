---
title: Crear un objeto agregado | Documentos de Microsoft
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
- aggregation [C++], creating aggregated objects
- aggregate objects [C++], creating
ms.assetid: fc29d7aa-fd53-4276-9c2f-37379f71b179
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7b6b66a80c5459157b644ec6b264b707232c83e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-aggregated-object"></a>Crear un objeto agregado
Los delegados de agregación **IUnknown** llamadas, proporcionando un puntero para el objeto externo **IUnknown** para el objeto interno.  
  
### <a name="to-create-an-aggregated-object"></a>Para crear un objeto agregado  
  
1.  Agregar un **IUnknown** puntero a la clase de objeto e inicialícela en **NULL** en el constructor.  
  
2.  Invalidar [FinalConstruct](../atl/reference/ccomobjectrootex-class.md#finalconstruct) para crear el agregado.  
  
3.  Use la **IUnknown** puntero, definido en el paso 1, como el segundo parámetro para el [COM_INTERFACE_ENTRY_AGGREGATE](reference/com-interface-entry-macros.md#com_interface_entry_aggregate) macros.  
  
4.  Invalidar [FinalRelease](../atl/reference/ccomobjectrootex-class.md#finalrelease) para liberar el **IUnknown** puntero.  
  
> [!NOTE]
>  Si usa y libera una interfaz del objeto agregado durante `FinalConstruct`, debe agregar el [macro DECLARE_PROTECT_FINAL_CONSTRUCT](reference/aggregation-and-class-factory-macros.md#declare_protect_final_construct) macro a la definición de su objeto de clase.  
  
## <a name="see-also"></a>Vea también  
 [Aspectos básicos de los objetos ATL COM](../atl/fundamentals-of-atl-com-objects.md)

