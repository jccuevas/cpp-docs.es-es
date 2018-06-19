---
title: Especificadores de invalidación (extensiones de componente de C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- override specifiers, Visual C++
- override specifiers
ms.assetid: 155bbf6f-4722-4654-afb1-9cb52af799fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4eb610157d1d56c00b48e98086137351e9fd43a8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33882767"
---
# <a name="override-specifiers--c-component-extensions"></a>Especificadores de invalidación (Extensiones de componentes de C++)
*Especificadores de invalidación* modificar cómo heredados tipos y miembros de tipos heredados se comportan en los tipos derivados.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 **Comentarios**  
  
 Para obtener más información acerca de los especificadores de invalidación, vea:  
  
-   [abstract](../windows/abstract-cpp-component-extensions.md)  
  
-   [New (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
-   [override](../windows/override-cpp-component-extensions.md)  
  
-   [sealed](../windows/sealed-cpp-component-extensions.md)  
  
-   [Especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md)  
  
 `abstract` y `sealed` también son válidos en declaraciones de tipos, donde no actúan como especificadores de invalidación.  
  
 Para obtener información sobre cómo reemplazar explícitamente funciones de clase base, vea [reemplazos explícitos](../windows/explicit-overrides-cpp-component-extensions.md).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 (No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime  
 (No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)