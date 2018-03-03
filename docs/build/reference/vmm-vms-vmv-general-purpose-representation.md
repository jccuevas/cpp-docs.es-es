---
title: "-vmm, - las máquinas virtuales, - vmv (representación de propósito General) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /vms
- /vmm
- /vmv
dev_langs:
- C++
helpviewer_keywords:
- Virtual Inheritance compiler option
- general purpose representation compiler options
- vms compiler option [C++]
- vmm compiler option [C++]
- /vmm compiler option [C++]
- -vmm compiler option [C++]
- -vms compiler option [C++]
- /vms compiler option [C++]
- vmv compiler option [C++]
- /vmv compiler option [C++]
- Single Inheritance compiler option
- -vmv compiler option [C++]
ms.assetid: 0fcd7ae0-3031-4c62-a2a8-e154c8685dae
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d54ea3cabbbe631006cc22a80fdbf500585ff20f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="vmm-vms-vmv-general-purpose-representation"></a>/vmm, /vms, /vmv (Representación de propósito general)
Se usa cuando [/vmb, /vmg (método de representación)](../../build/reference/vmb-vmg-representation-method.md) está seleccionado como el [método de representación](../../build/reference/vmb-vmg-representation-method.md). Estas opciones indican el modelo de herencia de la definición de clase aún no encontrada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/vmm  
/vms  
/vmv  
```  
  
## <a name="remarks"></a>Comentarios  
 Estas opciones se describen en la siguiente tabla.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**/ VMM**|Especifica la representación más general de un puntero a un miembro de una clase como aquella que utiliza herencia múltiple.<br /><br /> El correspondiente [palabra clave de herencia](../../cpp/inheritance-keywords.md) y el argumento [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) es **multiple_inheritance**.<br /><br /> Esta representación es mayor que el necesario para la herencia simple.<br /><br /> Si el modelo de herencia de una definición de clase para el que se declara un puntero a un miembro es virtual, el compilador genera un error.|  
|**VMM**|Especifica la representación más general de un puntero a un miembro de una clase como aquella que no usa ninguna herencia o herencia única.<br /><br /> El correspondiente [palabra clave de herencia](../../cpp/inheritance-keywords.md) y el argumento [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) es **herencia única**.<br /><br /> Se trata de la representación más pequeña posible de un puntero a un miembro de una clase.<br /><br /> Si el modelo de herencia de una definición de clase para el que se declara un puntero a un miembro es múltiple o virtual, el compilador genera un error.|  
|**/vmv**|Especifica la representación más general de un puntero a un miembro de una clase como aquella que utiliza herencia virtual. Nunca se produce un error y es el valor predeterminado.<br /><br /> El correspondiente [palabra clave de herencia](../../cpp/inheritance-keywords.md) y el argumento [#pragma pointers_to_members](../../preprocessor/pointers-to-members.md) es **virtual_inheritance**.<br /><br /> Esta opción requiere un puntero de mayor tamaño y el código adicional para interpretar el puntero que las otras opciones.|  
  
 Cuando se especifica una de estas opciones de modelo de herencia, ese modelo se utiliza para todos los punteros a miembros de clase, independientemente de su tipo de herencia o de si el puntero se declara antes o después de la clase. Por lo tanto, si siempre utiliza clases de herencia única, puede reducir el tamaño del código al compilar con **VMM**; sin embargo, si desea usar el caso más general (a expensas de la representación de datos más grande), compile con **/vmv**.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [/ vmb, /vmg (método de representación)](../../build/reference/vmb-vmg-representation-method.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)