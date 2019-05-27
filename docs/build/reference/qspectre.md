---
title: /Qspectre
ms.date: 10/12/2018
f1_keywords:
- /Qspectre
helpviewer_keywords:
- /Qspectre
ms.openlocfilehash: e44416a44a9f772c17bc734d26c62ff87be775c8
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837416"
---
# <a name="qspectre"></a>/Qspectre

Especifica la generación de instrucciones del compilador para mitigar determinadas vulnerabilidades de seguridad de la variante 1 de Spectre.

## <a name="syntax"></a>Sintaxis

> **/Qspectre**

## <a name="remarks"></a>Comentarios

La opción **/Qspectre** está disponible en la versión 15.5.5 de Visual Studio 2017 y versiones posteriores, y en Visual Studio 2015 Update 3 a través de [KB 4338871](https://support.microsoft.com/help/4338871/visual-studio-2015-update-3-spectre-variant-1-toolset-qspectre). Hace que el compilador inserte instrucciones para mitigar determinadas [vulnerabilidades de seguridad de Spectre](https://spectreattack.com/spectre.pdf). Estas vulnerabilidades, llamadas *ataques de canal lateral de ejecución especulativa*, afectan a muchos sistemas operativos y procesadores modernos, incluidos los procesadores de Intel, AMD y ARM.

La opción **/Qspectre** está desactivada de forma predeterminada.

En su versión inicial, la opción **/Qspectre** solo funcionaba en código optimizado. En Visual Studio 2017 versión 15.7 y posteriores, la opción **/Qspectre** se admite en todos los niveles de optimización.

También hay versiones con mitigación de Spectre de bibliotecas de Microsoft Visual C++. Las bibliotecas de Spectre mitigadas para Visual Studio 2017 y versiones posteriores se pueden descargar en el instalador de Visual Studio. Se encuentran en la pestaña **Componentes individuales**, bajo **Compiladores, herramientas de compilación y entornos de ejecución**, e incluyen "Libs for Spectre" (Bibliotecas para Spectre) en el nombre. Hay bibliotecas de tiempo de ejecución estáticas y DLL con mitigación habilitada disponibles para un subconjunto de los runtimes de Visual C++: código de inicio de VC++, vcruntime140, msvcp140, concrt140 y vcamp140. Los archivos DLL solo se admiten para la implementación de aplicaciones locales; el contenido del componente redistribuible de bibliotecas en tiempo de ejecución de Visual C++ 2017 y versiones posteriores no se ha modificado. También puede instalar bibliotecas de Spectre mitigadas para MFC y ATL, que se encuentran en la pestaña **Componentes individuales**, bajo **SDK, bibliotecas y marcos**.

### <a name="applicability"></a>Aplicabilidad

Si el código funciona en datos que cruzan un límite de confianza, se recomienda usar la opción **/Qspectre** para volver a compilar e implementar el código con el fin de mitigar este problema lo antes posible. Entre los ejemplos de código que funciona con datos que cruzan un límite de confianza se incluye el código que carga entradas que no son de confianza que pueden afectar a la ejecución, el que realiza llamadas a procedimientos remotos, que analiza entradas o archivos que no son de confianza, o bien que usa otras interfaces locales de comunicación entre procesos (IPC). Es posible que las técnicas estándar de espacio aislado no sean suficientes. Debe investigar con atención los espacios aislados antes de decidir que el código no cruza un límite de confianza.

### <a name="availability"></a>Disponibilidad

La opción **/Qspectre** está disponible en la versión 15.5.5 de Visual Studio 2017 y en todas las actualizaciones de los compiladores MSVC de Microsoft (MSVC) realizadas el 23 de enero de 2018 o después. Use el instalador de Visual Studio para actualizar el compilador y para instalar las bibliotecas de Spectre mitigadas como componentes individuales. La opción **/Qspectre** también está disponible en Visual Studio 2015 Update 3 a través de una revisión. Para más información, vea [KB 4338871](https://support.microsoft.com/help/4338871).

Todas las versiones de Visual Studio 2017 versión 15.5 y todas las versiones preliminares de Visual Studio 2017 versión 15.6 incluyen una opción sin documentar ( **/d2guardspecload**) que es equivalente al comportamiento inicial de **/Qspectre**. Puede usar **/d2guardspecload** para aplicar la mismas mitigaciones al código en estas versiones del compilador. Actualice la compilación para usar **/Qspectre** en los compiladores que admiten la opción; la opción **/Qspectre** también puede admitir mitigaciones nuevas en versiones posteriores del compilador.

### <a name="effect"></a>Efecto

La opción **/Qspectre** genera código para mitigar la variante 1 de Spectre, Derivación de comprobación de límites, [CVE-2017-5753](https://nvd.nist.gov/vuln/detail/CVE-2017-5753). Funciona mediante la inserción de instrucciones que actúan como una barrera de ejecución de código especulativo. Las instrucciones específicas que se usan para mitigar la especulación de procesador dependen del procesador y su microarquitectura, y pueden cambiar en versiones futuras del compilador.

Cuando se habilita la opción **/Qspectre**, el compilador intenta identificar instancias donde la ejecución especulativa puede omitir las comprobaciones de límites e inserta las instrucciones de barrera. Es importante tener en cuenta que hay límites con respecto al análisis que puede realizar un compilador para identificar las instancias de la variante 1. Por tanto, no hay ninguna garantía de que todos los posibles casos de la variante 1 se instrumenten bajo **/Qspectre**.

### <a name="performance-impact"></a>Impacto del rendimiento

Se ha comprobado que el impacto de rendimiento de **/Qspectre** es insignificante en varias bases de código de gran tamaño, pero no hay ninguna garantía de que el rendimiento del código bajo **/Qspectre** no se vea afectado. Debe realizar pruebas comparativas del código para determinar el efecto de la opción en el rendimiento. Si sabe que la mitigación no es necesaria en un bucle o bloque crítico para el rendimiento, se puede deshabilitar de forma selectiva mediante una directiva [__declspec(spectre(nomitigation))](../../cpp/spectre.md). Esta directiva no está disponible en los compiladores que solo admiten la opción **/d2guardspecload**.

### <a name="required-libraries"></a>Bibliotecas necesarias

La opción del compilador **/Qspectre** genera código que vincula de forma implícita las versiones de las bibliotecas en tiempo de ejecución que se han creado para proporcionar las mitigaciones de Spectre. Estas bibliotecas son componentes opcionales que se deben instalar mediante el instalador de Visual Studio:

- Versión de MSVC *números_de_versión* Bibliotecas para Spectre \[(x86 y x64) | (ARM) | (ARM64)]
- ATL de Visual C++ para \[(x86/x64) | ARM | ARM64] con mitigaciones de Spectre
- MFC de Visual C++ para \[(x86/x64) | ARM | ARM64] con mitigaciones de Spectre

Si compila el código mediante **/Qspectre** y estas bibliotecas no están instaladas, el sistema de compilación notifica la **advertencia MSB8038: La mitigación de Spectre está habilitada pero no se han encontrado bibliotecas de Spectre mitigadas**. Si se produce un error en la compilación del código de MFC o ATL, y el enlazador informa de un error como **error irrecuperable LNK1104: no se puede abrir el archivo "oldnames.lib"** , estas bibliotecas que faltan pueden ser la causa.

### <a name="additional-information"></a>Información adicional

Para más información, vea el sitio oficial [Microsoft Security Advisory ADV180002, Guidance to mitigate speculative execution side-channel vulnerabilities](https://portal.msrc.microsoft.com/en-US/security-guidance/advisory/ADV180002) (Instrucciones para mitigar los ataques de canal lateral de ejecución especulativa). También hay instrucciones de Intel, [Speculative Execution Side Channel Mitigations](https://software.intel.com/sites/default/files/managed/c5/63/336996-Speculative-Execution-Side-Channel-Mitigations.pdf) (Mitigaciones de canal lateral de ejecución especulativa) y ARM, [Cache Speculation Side-channels](https://developer.arm.com/-/media/Files/pdf/Cache_Speculation_Side-channels.pdf) (Almacenamiento en caché de canales de ejecución especulativa). Para obtener información específica de Windows sobre las mitigaciones de Spectre y Meltdown, vea [Understanding the performance impact of Spectre and Meltdown mitigations on Windows Systems](https://cloudblogs.microsoft.com/microsoftsecure/2018/01/09/understanding-the-performance-impact-of-spectre-and-meltdown-mitigations-on-windows-systems/) (Descripción del impacto de rendimiento de las mitigaciones de Spectre y Meltdown en sistemas Windows) en el blog de Microsoft Secure. Para obtener información general de las vulnerabilidades de Spectre solucionadas por las mitigaciones de MSVC, vea [Spectre mitigations in MSVC](https://blogs.msdn.microsoft.com/vcblog/2018/01/15/spectre-mitigations-in-msvc./) (Mitigaciones de Spectre en MSVC) en el blog del equipo de Visual C++.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C /C++** > **Línea de comandos**.

1. Escriba la opción del compilador **/Qspectre** en el cuadro **Opciones adicionales**. Seleccione **Aceptar** para aplicar el cambio.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/Q (Opciones) (Operaciones de bajo nivel)](q-options-low-level-operations.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
