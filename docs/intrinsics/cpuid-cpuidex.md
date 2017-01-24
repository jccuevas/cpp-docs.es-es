---
title: "__cpuid, __cpuidex | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__cpuid_cpp"
  - "__cpuid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__cpuid intrinsic"
  - "cpuid instruction"
  - "cpuid intrinsic"
ms.assetid: f8c344d3-91bf-405f-8622-cb0e337a6bdc
caps.latest.revision: 38
caps.handback.revision: 36
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __cpuid, __cpuidex
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 Genera la instrucción `cpuid` que está disponible en x86 y [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)].  Esta instrucción realiza una consulta al procesador para obtener información sobre las características admitidas y el tipo de CPU.  
  
## Sintaxis  
  
```  
void __cpuid(  
   int cpuInfo[4],  
   int function_id  
);  
  
void __cpuidex(  
   int cpuInfo[4],  
   int function_id,  
   int subfunction_id  
);  
```  
  
#### Parámetros  
 \[out\] `cpuInfo`  
 Matriz de cuatro enteros que contiene la información devuelta en EAX, EBX, ECX y EDX sobre las características admitidas de la CPU.  
  
 \[in\] `function_id`  
 Código que especifica la información que se va recuperar, pasada en EAX.  
  
 \[in\] `subfunction_id`  
 Código extra que especifica la información que se va recuperar, pasada en ECX.  
  
## Requisitos  
  
|Función intrínseca|Arquitectura|  
|------------------------|------------------|  
|`__cpuid`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
|`__cpuidex`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Archivo de encabezado** \<intrin.h\>  
  
## Comentarios  
 Esta función intrínseca almacena las características compatibles y la información de la CPU que la instrucción `cpuid` devuelve en `cpuInfo`, una matriz de cuatro enteros de 32 bits que se rellena con los valores de los registros EAX, EBX, ECX y EDX \(en ese orden\).  El significado de la información devuelta varía en función del valor que se ha pasado como parámetro de `function_id`.  La información que se devuelve con varios valores de `function_id` depende del procesador.  
  
 La función intrínseca `__cpuid` borra el registro ECX antes de llamar a la instrucción `cpuid`.  La función intrínseca `__cpuidex` establece el valor del registro ECX en `subfunction_id` antes de generar la instrucción `cpuid`.  Esto permite recabar más información sobre el procesador.  
  
 Para obtener más información sobre los parámetros específicos que deben usarse y los valores que devuelven estos intrínsecos en procesadores Intel, consulte la documentación relativa a la instrucción `cpuid` en la [referencia sobre conjuntos de instrucciones del volumen de manual 2 para desarrolladores de software de arquitecturas de Intel 64 e IA32](http://go.microsoft.com/fwlink/p/?LinkID=510021) y la [referencia sobre la programación de extensiones de conjuntos de instrucciones de arquitectura de Intel](http://go.microsoft.com/fwlink/p/?LinkID=506627).  En la documentación de Intel se emplean los términos "hoja" y "subhoja" en relación con los parámetros `function_id` y `subfunction_id` que se pasan en EAX y ECX.  
  
 Para obtener más información sobre los parámetros específicos que se deben usar y los valores que estos intrínsecos devuelven en relación con los procesadores AMD, consulte la documentación relativa a la instrucción `cpuid` en las [instrucciones de sistema y de carácter general del volumen de manual 3 para programadores de arquitecturas AMD64](http://go.microsoft.com/fwlink/p/?LinkId=510023) y en las [guías de revisión](http://go.microsoft.com/fwlink/p/?LinkId=510023) para las familias de procesadores específicos.  En la documentación de AMD se emplean los términos "número de función" y "número de subfunción" en relación con los parámetros `function_id` y `subfunction_id` que se pasan en EAX y ECX.  
  
 Cuando el argumento `function_id` es 0, `cpuInfo[0]` devuelve el mejor `function_id` no ampliado disponible que es compatible con el procesador.  El fabricante del procesador está codificado en `cpuInfo[1]`, `cpuInfo[2]` y cpuInfo\[3\].  
  
 La compatibilidad para extensiones de conjuntos de instrucciones específicas y características de la CPU está codificada en los resultados `cpuInfo` que se devuelven para los valores de function\_id más altos.  Para obtener más información, consulte los manuales indicados anteriormente y el siguiente código de ejemplo.  
  
 Algunos procesadores admiten la información de CPUID de función ampliada.  Si así es, se pueden usar valores de `function_id` de 0x80000000 para obtener información.  Para fijar el valor máximo con significado permitido, establezca `function_id` en 0x80000000.  El valor máximo de `function_id` permitido para las funciones ampliadas quedará registrado en `cpuInfo[0]`.  
  
## Ejemplo  
 En este ejemplo se muestra parte de la información disponible a través de los intrínsecos `__cpuid` y `__cpuidex`.  La aplicación muestra las extensiones de conjuntos de instrucciones compatibles con el procesador actual.  El resultado muestra un resultado posible de un procesador en particular.  
  
```  
// InstructionSet.cpp   
// Compile by using: cl /EHsc /W4 InstructionSet.cpp  
// processor: x86, x64  
// Uses the __cpuid intrinsic to get information about   
// CPU extended instruction set support.  
  
#include <iostream>  
#include <vector>  
#include <bitset>  
#include <array>  
#include <string>  
#include <intrin.h>  
  
class InstructionSet  
{  
    // forward declarations  
    class InstructionSet_Internal;  
  
public:  
    // getters  
    static std::string Vendor(void) { return CPU_Rep.vendor_; }  
    static std::string Brand(void) { return CPU_Rep.brand_; }  
  
    static bool SSE3(void) { return CPU_Rep.f_1_ECX_[0]; }  
    static bool PCLMULQDQ(void) { return CPU_Rep.f_1_ECX_[1]; }  
    static bool MONITOR(void) { return CPU_Rep.f_1_ECX_[3]; }  
    static bool SSSE3(void) { return CPU_Rep.f_1_ECX_[9]; }  
    static bool FMA(void) { return CPU_Rep.f_1_ECX_[12]; }  
    static bool CMPXCHG16B(void) { return CPU_Rep.f_1_ECX_[13]; }  
    static bool SSE41(void) { return CPU_Rep.f_1_ECX_[19]; }  
    static bool SSE42(void) { return CPU_Rep.f_1_ECX_[20]; }  
    static bool MOVBE(void) { return CPU_Rep.f_1_ECX_[22]; }  
    static bool POPCNT(void) { return CPU_Rep.f_1_ECX_[23]; }  
    static bool AES(void) { return CPU_Rep.f_1_ECX_[25]; }  
    static bool XSAVE(void) { return CPU_Rep.f_1_ECX_[26]; }  
    static bool OSXSAVE(void) { return CPU_Rep.f_1_ECX_[27]; }  
    static bool AVX(void) { return CPU_Rep.f_1_ECX_[28]; }  
    static bool F16C(void) { return CPU_Rep.f_1_ECX_[29]; }  
    static bool RDRAND(void) { return CPU_Rep.f_1_ECX_[30]; }  
  
    static bool MSR(void) { return CPU_Rep.f_1_EDX_[5]; }  
    static bool CX8(void) { return CPU_Rep.f_1_EDX_[8]; }  
    static bool SEP(void) { return CPU_Rep.f_1_EDX_[11]; }  
    static bool CMOV(void) { return CPU_Rep.f_1_EDX_[15]; }  
    static bool CLFSH(void) { return CPU_Rep.f_1_EDX_[19]; }  
    static bool MMX(void) { return CPU_Rep.f_1_EDX_[23]; }  
    static bool FXSR(void) { return CPU_Rep.f_1_EDX_[24]; }  
    static bool SSE(void) { return CPU_Rep.f_1_EDX_[25]; }  
    static bool SSE2(void) { return CPU_Rep.f_1_EDX_[26]; }  
  
    static bool FSGSBASE(void) { return CPU_Rep.f_7_EBX_[0]; }  
    static bool BMI1(void) { return CPU_Rep.f_7_EBX_[3]; }  
    static bool HLE(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_7_EBX_[4]; }  
    static bool AVX2(void) { return CPU_Rep.f_7_EBX_[5]; }  
    static bool BMI2(void) { return CPU_Rep.f_7_EBX_[8]; }  
    static bool ERMS(void) { return CPU_Rep.f_7_EBX_[9]; }  
    static bool INVPCID(void) { return CPU_Rep.f_7_EBX_[10]; }  
    static bool RTM(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_7_EBX_[11]; }  
    static bool AVX512F(void) { return CPU_Rep.f_7_EBX_[16]; }  
    static bool RDSEED(void) { return CPU_Rep.f_7_EBX_[18]; }  
    static bool ADX(void) { return CPU_Rep.f_7_EBX_[19]; }  
    static bool AVX512PF(void) { return CPU_Rep.f_7_EBX_[26]; }  
    static bool AVX512ER(void) { return CPU_Rep.f_7_EBX_[27]; }  
    static bool AVX512CD(void) { return CPU_Rep.f_7_EBX_[28]; }  
    static bool SHA(void) { return CPU_Rep.f_7_EBX_[29]; }  
  
    static bool PREFETCHWT1(void) { return CPU_Rep.f_7_ECX_[0]; }  
  
    static bool LAHF(void) { return CPU_Rep.f_81_ECX_[0]; }  
    static bool LZCNT(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_ECX_[5]; }  
    static bool ABM(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[5]; }  
    static bool SSE4a(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[6]; }  
    static bool XOP(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[11]; }  
    static bool TBM(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_ECX_[21]; }  
  
    static bool SYSCALL(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_EDX_[11]; }  
    static bool MMXEXT(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[22]; }  
    static bool RDTSCP(void) { return CPU_Rep.isIntel_ && CPU_Rep.f_81_EDX_[27]; }  
    static bool _3DNOWEXT(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[30]; }  
    static bool _3DNOW(void) { return CPU_Rep.isAMD_ && CPU_Rep.f_81_EDX_[31]; }  
  
private:  
    static const InstructionSet_Internal CPU_Rep;  
  
    class InstructionSet_Internal  
    {  
    public:  
        InstructionSet_Internal()  
            : nIds_{ 0 },  
            nExIds_{ 0 },  
            isIntel_{ false },  
            isAMD_{ false },  
            f_1_ECX_{ 0 },  
            f_1_EDX_{ 0 },  
            f_7_EBX_{ 0 },  
            f_7_ECX_{ 0 },  
            f_81_ECX_{ 0 },  
            f_81_EDX_{ 0 },  
            data_{},  
            extdata_{}  
        {  
            //int cpuInfo[4] = {-1};  
            std::array<int, 4> cpui;  
  
            // Calling __cpuid with 0x0 as the function_id argument  
            // gets the number of the highest valid function ID.  
            __cpuid(cpui.data(), 0);  
            nIds_ = cpui[0];  
  
            for (int i = 0; i <= nIds_; ++i)  
            {  
                __cpuidex(cpui.data(), i, 0);  
                data_.push_back(cpui);  
            }  
  
            // Capture vendor string  
            char vendor[0x20];  
            memset(vendor, 0, sizeof(vendor));  
            *reinterpret_cast<int*>(vendor) = data_[0][1];  
            *reinterpret_cast<int*>(vendor + 4) = data_[0][3];  
            *reinterpret_cast<int*>(vendor + 8) = data_[0][2];  
            vendor_ = vendor;  
            if (vendor_ == "GenuineIntel")  
            {  
                isIntel_ = true;  
            }  
            else if (vendor_ == "AuthenticAMD")  
            {  
                isAMD_ = true;  
            }  
  
            // load bitset with flags for function 0x00000001  
            if (nIds_ >= 1)  
            {  
                f_1_ECX_ = data_[1][2];  
                f_1_EDX_ = data_[1][3];  
            }  
  
            // load bitset with flags for function 0x00000007  
            if (nIds_ >= 7)  
            {  
                f_7_EBX_ = data_[7][1];  
                f_7_ECX_ = data_[7][2];  
            }  
  
            // Calling __cpuid with 0x80000000 as the function_id argument  
            // gets the number of the highest valid extended ID.  
            __cpuid(cpui.data(), 0x80000000);  
            nExIds_ = cpui[0];  
  
            char brand[0x40];  
            memset(brand, 0, sizeof(brand));  
  
            for (int i = 0x80000000; i <= nExIds_; ++i)  
            {  
                __cpuidex(cpui.data(), i, 0);  
                extdata_.push_back(cpui);  
            }  
  
            // load bitset with flags for function 0x80000001  
            if (nExIds_ >= 0x80000001)  
            {  
                f_81_ECX_ = extdata_[1][2];  
                f_81_EDX_ = extdata_[1][3];  
            }  
  
            // Interpret CPU brand string if reported  
            if (nExIds_ >= 0x80000004)  
            {  
                memcpy(brand, extdata_[2].data(), sizeof(cpui));  
                memcpy(brand + 16, extdata_[3].data(), sizeof(cpui));  
                memcpy(brand + 32, extdata_[4].data(), sizeof(cpui));  
                brand_ = brand;  
            }  
        };  
  
        int nIds_;  
        int nExIds_;  
        std::string vendor_;  
        std::string brand_;  
        bool isIntel_;  
        bool isAMD_;  
        std::bitset<32> f_1_ECX_;  
        std::bitset<32> f_1_EDX_;  
        std::bitset<32> f_7_EBX_;  
        std::bitset<32> f_7_ECX_;  
        std::bitset<32> f_81_ECX_;  
        std::bitset<32> f_81_EDX_;  
        std::vector<std::array<int, 4>> data_;  
        std::vector<std::array<int, 4>> extdata_;  
    };  
};  
  
// Initialize static member data  
const InstructionSet::InstructionSet_Internal InstructionSet::CPU_Rep;  
  
// Print out supported instruction set extensions  
int main()  
{  
    auto& outstream = std::cout;  
  
    auto support_message = [&outstream](std::string isa_feature, bool is_supported) {  
        outstream << isa_feature << (is_supported ? " supported" : " not supported") << std::endl;  
    };  
  
    std::cout << InstructionSet::Vendor() << std::endl;  
    std::cout << InstructionSet::Brand() << std::endl;  
  
    support_message("3DNOW",       InstructionSet::_3DNOW());  
    support_message("3DNOWEXT",    InstructionSet::_3DNOWEXT());  
    support_message("ABM",         InstructionSet::ABM());  
    support_message("ADX",         InstructionSet::ADX());  
    support_message("AES",         InstructionSet::AES());  
    support_message("AVX",         InstructionSet::AVX());  
    support_message("AVX2",        InstructionSet::AVX2());  
    support_message("AVX512CD",    InstructionSet::AVX512CD());  
    support_message("AVX512ER",    InstructionSet::AVX512ER());  
    support_message("AVX512F",     InstructionSet::AVX512F());  
    support_message("AVX512PF",    InstructionSet::AVX512PF());  
    support_message("BMI1",        InstructionSet::BMI1());  
    support_message("BMI2",        InstructionSet::BMI2());  
    support_message("CLFSH",       InstructionSet::CLFSH());  
    support_message("CMPXCHG16B",  InstructionSet::CMPXCHG16B());  
    support_message("CX8",         InstructionSet::CX8());  
    support_message("ERMS",        InstructionSet::ERMS());  
    support_message("F16C",        InstructionSet::F16C());  
    support_message("FMA",         InstructionSet::FMA());  
    support_message("FSGSBASE",    InstructionSet::FSGSBASE());  
    support_message("FXSR",        InstructionSet::FXSR());  
    support_message("HLE",         InstructionSet::HLE());  
    support_message("INVPCID",     InstructionSet::INVPCID());  
    support_message("LAHF",        InstructionSet::LAHF());  
    support_message("LZCNT",       InstructionSet::LZCNT());  
    support_message("MMX",         InstructionSet::MMX());  
    support_message("MMXEXT",      InstructionSet::MMXEXT());  
    support_message("MONITOR",     InstructionSet::MONITOR());  
    support_message("MOVBE",       InstructionSet::MOVBE());  
    support_message("MSR",         InstructionSet::MSR());  
    support_message("OSXSAVE",     InstructionSet::OSXSAVE());  
    support_message("PCLMULQDQ",   InstructionSet::PCLMULQDQ());  
    support_message("POPCNT",      InstructionSet::POPCNT());  
    support_message("PREFETCHWT1", InstructionSet::PREFETCHWT1());  
    support_message("RDRAND",      InstructionSet::RDRAND());  
    support_message("RDSEED",      InstructionSet::RDSEED());  
    support_message("RDTSCP",      InstructionSet::RDTSCP());  
    support_message("RTM",         InstructionSet::RTM());  
    support_message("SEP",         InstructionSet::SEP());  
    support_message("SHA",         InstructionSet::SHA());  
    support_message("SSE",         InstructionSet::SSE());  
    support_message("SSE2",        InstructionSet::SSE2());  
    support_message("SSE3",        InstructionSet::SSE3());  
    support_message("SSE4.1",      InstructionSet::SSE41());  
    support_message("SSE4.2",      InstructionSet::SSE42());  
    support_message("SSE4a",       InstructionSet::SSE4a());  
    support_message("SSSE3",       InstructionSet::SSSE3());  
    support_message("SYSCALL",     InstructionSet::SYSCALL());  
    support_message("TBM",         InstructionSet::TBM());  
    support_message("XOP",         InstructionSet::XOP());  
    support_message("XSAVE",       InstructionSet::XSAVE());  
}  
```  
  
  **GenuineIntel**  
 **Intel\(R\) Core\(TM\) i5\-2500 CPU a 3,30 GHz**  
**3DNOW no compatible**  
**3DNOWEXT no compatible**  
**ABN no compatible**  
**ADX no compatible**  
**AES compatible**  
**AVX compatible**  
**AVX2 no compatible**  
**AVX512CD no compatible**  
**AVX512ER no compatible**  
**AVX512F no compatible**  
**AVX512PF no compatible**  
**BMI1 no compatible**  
**BMI2 no compatible**  
**CLFSH compatible**  
**CMPXCHG16B compatible**  
**CX8 compatible**  
**ERMS no compatible**  
**F16C no compatible**  
**FMA no compatible**  
**FSGSBASE no compatible**  
**FXSR compatible**  
**HLE no compatible**  
**INVPCID no compatible**  
**LAHF compatible**  
**LZCNT no compatible**  
**MMX compatible**  
**MMXEXT no compatible**  
**MONITOR no compatible**  
**MOVBE no compatible**  
**MSR compatible**  
**OSXSAVE compatible**  
**PCLMULQDQ compatible**  
**POPCNT compatible**  
**PREFETCHWT1 no compatible**  
**RDRAND no compatible**  
**RDSEED no compatible**  
**RDTSCP compatible**  
**RTM no compatible**  
**SEP compatible**  
**SHA no compatible**  
**SSE compatible**  
**SSE2 compatible**  
**SSE3 compatible**  
**SSE4.1 compatible**  
**SSE4.2 compatible**  
**SSE4a no compatible**  
**SSSE3 compatible**  
**SYSCALL compatible**  
**TBM no compatible**  
**XOP no compatible**  
**XSAVE compatible**   
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)