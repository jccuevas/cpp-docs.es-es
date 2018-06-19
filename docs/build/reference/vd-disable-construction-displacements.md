---
title: -vd (deshabilitar desplazamientos de constructores) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /vd
dev_langs:
- C++
helpviewer_keywords:
- -vd0 compiler option [C++]
- vd1 compiler option [C++]
- /vdn (Disable Construction Displacement) compiler option
- constructor displacements
- vtordisp fields
- /vd0 compiler option [C++]
- -vd1 compiler option [C++]
- /vd1 compiler option [C++]
- displacements compiler option
- vd0 compiler option [C++]
- Disable Construction Displacements compiler option
ms.assetid: 93258964-14d7-4b1c-9cbc-d6f4d74eab69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6a7b9bacc95c668c1c0f59a3dba172d58c607d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377602"
---
# <a name="vd-disable-construction-displacements"></a>/vd (Deshabilitar desplazamientos de constructores)
## <a name="syntax"></a>Sintaxis  
  
```  
/vdn  
```  
  
## <a name="arguments"></a>Argumentos  
 `0`  
 Suprime al miembro constructor/destructor de vtordisp. Elija esta opción sólo si está seguro de que todos los constructores de clase y destructores llame virtuales funciona prácticamente.  
  
 `1`  
 Habilita la creación de los miembros de desplazamiento de constructor/destructor de vtordisp ocultos. Esta opción es el valor predeterminado.  
  
 `2`  
 Le permite usar [dynamic_cast (operador)](../../cpp/dynamic-cast-operator.md) en un objeto que se está construyendo. Por ejemplo, un dynamic_cast de una clase base virtual a una clase derivada.  
  
 **/ vd2** agrega un campo vtordisp cuando tenga una base virtual con funciones virtuales. **/ vd1** debería ser suficiente. La más común caso where **/vd2** es necesario es cuando la función virtual solo en la base virtual es un destructor.  
  
## <a name="remarks"></a>Comentarios  
 Estas opciones se aplican únicamente al código de C++ que usa bases virtuales.  
  
 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] implementa la compatibilidad con desplazamiento de construcción de C++ en situaciones donde se utiliza herencia virtual. Desplazamientos de constructores resuelve el problema que se crea cuando una función virtual, declarada en una base virtual y se reemplaza en una clase derivada, se llama desde un constructor durante la construcción de una clase derivada posterior.  
  
 El problema es que la función virtual se puede pasar incorrecta `this` puntero como resultado de las diferencias entre los desplazamientos de virtual basa la base de una clase y los desplazamientos de sus clases derivadas. La solución proporciona un ajuste de desplazamiento de construcción único, denominado campo vtordisp, para cada base virtual de una clase.  
  
 De forma predeterminada, los campos de vtordisp se introducen siempre que el código define los destructores y los constructores definidos por el usuario y también reemplaza a funciones virtuales de bases virtuales.  
  
 Estas opciones afecta a los archivos de código fuente. Use [vtordisp](../../preprocessor/vtordisp.md) suprimir y, a continuación, volver a habilitar campos vtordisp clase por clase.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Haga clic en la carpeta **C/C++** .  
  
3.  Haga clic en la página de propiedades **Línea de comandos** .  
  
4.  Escriba la opción del compilador en el cuadro **Opciones adicionales** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)