---
title: -protección (Habilitar protección de flujo de Control) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /guard
- VC.Project.VCCLCompilerTool.ControlFlowGuard
dev_langs:
- C++
ms.assetid: be495323-f59f-4cf3-a6b6-8ee69e6a19dd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5c60ff444189e9e6b7919b43649b75722ee7249
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="guard-enable-control-flow-guard"></a>/guard (habilitar Protección de flujo de control)
Habilite la generación del compilador de comprobaciones de seguridad de Protección de flujo de control.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/guard:cf[-]  
```  
  
## <a name="remarks"></a>Comentarios  
 La opción **/guard:cf** hace que el compilador analice el flujo de control para los destinos de llamada indirecta en tiempo de compilación y que después inserte código para comprobar los destinos en tiempo de ejecución. La opción **/guard:cf** está desactivada de forma predeterminada y debe habilitarse explícitamente. Para deshabilitar explícitamente esta opción, utilice **/guard:cf-**.  
  
 Cuando la opción de Protección de flujo de control (CFG) **/guard:cf** se especifica, el compilador y el vinculador insertan comprobaciones de seguridad en tiempo de ejecución adicionales para detectar aquellas acciones que pretenden poner en peligro su código. Durante la compilación y vinculación, se analizan todas las llamadas indirectas en el código para encontrar todas las ubicaciones que puede alcanzar el código cuando se ejecuta correctamente. Esta información se almacena en estructuras adicionales en los encabezados de los archivos binarios. El compilador también inserta una comprobación antes de cada llamada indirecta en el código, que garantiza que el destino sea una de las ubicaciones comprobadas. Si se produce un error en la comprobación en tiempo de ejecución en un sistema operativo compatible con CFG, el sistema operativo cierra el programa.  
  
 Un ataque habitual al software aprovecha los errores en el control de entradas extremas o inesperadas. Una entrada cuidadosamente implementada en la aplicación podría sobrescribir una ubicación que contenga un puntero a código ejecutable. Esto puede utilizarse para redirigir el flujo de control al código controlado por el atacante. Las comprobaciones en tiempo de ejecución de CFG no corrigen los errores de daños en los datos que tenga su ejecutable. En su lugar, hacen que sea más difícil para los atacantes utilizarlos para ejecutar código arbitrario. CFG es una herramienta de mitigación que evita llamadas a otras ubicaciones que no sean puntos de entrada de función en el código. Es similar a cómo la prevención de ejecución de datos (DEP),  [/GS](../../build/reference/gs-buffer-security-check.md) las comprobaciones de pila y la selección aleatoria de diseño de espacio de direcciones (ASLR) de [/DYNAMICBASE](../../build/reference/dynamicbase-use-address-space-layout-randomization.md) y [/HIGHENTROPYVA](../../build/reference/highentropyva-support-64-bit-aslr.md) reducen las posibilidades de que el código se convierta un vector de vulnerabilidad de seguridad.  
  
 La opción **/guard:cf** debe pasarse tanto al compilador como al vinculador para compilar código que use la técnica de mitigación de vulnerabilidad de seguridad de CFG. Si el archivo binario se compila mediante un único comando `cl` , el compilador pasa la opción al vinculador. Si compila y vincula por separado, la opción debe establecerse tanto en los comandos del compilador como del vinculador. También se requiere la opción del vinculador /DYNAMICBASE. Para comprobar que su binario tenga datos CFG, use el comando `dumpbin /headers /loadconfig` . Los binarios con CFG tienen `Guard` en la lista de características EXE o DLL y los indicadores de protección incluyen `CF Instrumented` y `FID table present`.  
  
 La opción **/guard:cf** es incompatible con la opción [/ZI](../../build/reference/z7-zi-zi-debug-information-format.md) (Editar y continuar información de depuración) o [/clr](../../build/reference/clr-common-language-runtime-compilation.md) (compilación de Common Language Runtime).  
  
 El código compilado mediante **/guard:cf** se puede vincular a bibliotecas y archivos de objeto que no estén compilados mediante el uso de esta opción. Solo este código, si también se vincula mediante la opción **/guard:cf** y se ejecuta en un sistema operativo compatible con CFG, está protegido mediante CFG. Dado que el código compilado sin esta opción no detendrá un ataque, se recomienda utilizar la opción en todo el código que se compile. Las comprobaciones de CFG tienen un pequeño coste en tiempo de ejecución, pero el análisis del compilador intenta optimizar las comprobaciones en saltos indirectos que se pueda demostrar que son seguros.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione **Propiedades de configuración**, **C/C++** y **Generación de código**.  
  
3.  Seleccione la propiedad **Protección de flujo de control** .  
  
4.  En el control desplegable, elija **Sí** para habilitar la Protección de flujo de control o **No** para deshabilitarla.  
  
## <a name="see-also"></a>Vea también  
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)