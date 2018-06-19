---
title: / Qspectre | Documentos de Microsoft
ms.custom: ''
ms.date: 1/23/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3d87850ae5413ccf876eb4d4b44b34e34527ef9a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379424"
---
# <a name="qspectre"></a>/ Qspectre

Especifica la generación de compilador de instrucciones para mitigar determinadas vulnerabilidades de seguridad de variante 1 Spectre.

## <a name="syntax"></a>Sintaxis

> **/Qspectre**

## <a name="remarks"></a>Comentarios

El **/Qspectre** opción hace que el compilador insertar instrucciones para mitigar determinados [vulnerabilidades de seguridad de Spectre](https://spectreattack.com/spectre.pdf). Estas vulnerabilidades, denominadas *ataques del lado de canal de ejecución especulativa*, afecta a muchos sistemas operativos y los procesadores modernos, incluidos los procesadores de Intel, AMD y ARM.

El **/Qspectre** opción está desactivada de forma predeterminada.

En su versión inicial, la **/Qspectre** opción solo funciona en código optimizado. Debe asegurarse de que al compilar el código con cualquiera de las opciones de optimización (por ejemplo, [/O2 o/O1](o1-o2-minimize-size-maximize-speed.md) pero no [/Od](od-disable-debug.md)) para asegurarse de que se aplica la mitigación. De forma similar, inspeccionar cualquier código que utilice [#pragma optimize ("stg", off)](../../preprocessor/optimize.md).

### <a name="applicability"></a>Aplicabilidad

Si el código funciona en los datos que atraviesen un límite de confianza, a continuación, le recomendamos que use la **/Qspectre** opción para volver a generar e implementar el código para mitigar este problema tan pronto como sea posible. Código que carga la entrada no es de confianza que puede afectar a la ejecución de ejemplos de código que funciona en los datos que atraviesen un límite de confianza, por ejemplo, código que realiza el procedimiento remoto llama, analiza la entrada no es de confianza o archivos o utiliza otros local entre procesos interfaces de comunicación entre procesos (IPC). Técnicas de espacio aislado estándar pueden no ser suficientes. Debería investigar los espacios aislados detenidamente antes de decidir que el código no atraviesa un límite de confianza.

### <a name="availability"></a>Disponibilidad

El **/Qspectre** opción está disponible en la versión de Visual Studio de 2017 15.5.5 y todas las actualizaciones a los compiladores de Microsoft Visual C++ (MSVC) realizadas en o después de 23 de enero de 2018.

Todas las versiones de la versión de Visual Studio de 2017 15.5 y todas las vistas previas de Visual Studio versión 15.6 ya incluye una opción sin documentar, **/d2guardspecload**, que es equivalente al comportamiento inicial de **/Qspectre**. Puede usar **/d2guardspecload** para aplicar la mismas mitigaciones para el código en estas versiones del compilador. Actualice la compilación para usar **/Qspectre** en los compiladores que admiten la opción; la **/Qspectre** opción también puede admitir mitigaciones de nuevo en versiones posteriores del compilador.

### <a name="effect"></a>Efecto

El **/Qspectre** opción genera código para mitigar la variante de espectro 1, omisión de comprobación de límites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funciona mediante la inserción de instrucciones que actúan como una barrera de ejecución de código especulativa. Las instrucciones específicas que se utiliza para mitigar especulación de procesador dependen del procesador y su arquitectura micro y pueden cambiar en futuras versiones del compilador.

Cuando el **/Qspectre** opción está habilitada, el compilador intenta identificar instancias en ejecución especulativa puede omitir las comprobaciones de los límites e inserta las instrucciones de barrera. Es importante tener en cuenta que no hay límite para el análisis que un compilador puede llevar a cabo para identificar las instancias de variante 1. Por lo tanto, no hay ninguna garantía de que todas las instancias posibles de variante 1 instrumentadas en **/Qspectre**.

### <a name="performance-impact"></a>Impacto en el rendimiento

El impacto del rendimiento **/Qspectre** se ha visto sea insignificante en varias bases de código muy grandes, pero no hay ninguna garantía de que el rendimiento del código sometido a **/Qspectre** no se ve afectado. Debe realicen pruebas comparativas de su código para determinar el efecto de la opción en el rendimiento. Si sabe que la mitigación no es necesario en un bucle o un bloque esenciales para el rendimiento, la mitigación se puede deshabilitar selectivamente mediante el uso de un [__declspec(spectre(nomitigation))](../../cpp/spectre.md) directiva. Esta directiva no está disponible en los compiladores que admiten solo el **/d2guardspecload** opción.

### <a name="additional-information"></a>Información adicional

Para obtener más información, consulte el oficial [ADV180002 de aviso de seguridad de Microsoft, la orientación para mitigar las vulnerabilidades del lado de canal de ejecución especulativa](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002). Guía también está disponible de Intel, [mitigaciones de canal de lado de ejecución especulativa](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf)y ARM, [canales del lado de especulación de caché](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf). Para obtener información específica de Windows de Spectre y colapso mitigaciones, consulte [entender el impacto de rendimiento de las mitigaciones Spectre y colapso en sistemas Windows](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) en el blog de Microsoft Secure. Para obtener información general de la vulnerabilidad de Spectre direccionada por las mitigaciones MSVC, consulte [mitigaciones Spectre en MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) en el Blog del equipo de Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Escriba el **/Qspectre** opción del compilador en el **opciones adicionales** cuadro. Elija **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](../../build/reference/q-options-low-level-operations.md)  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
