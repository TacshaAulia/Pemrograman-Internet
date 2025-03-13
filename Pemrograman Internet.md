# Pemrograman-Internet

//adminlogin
export default function Page() {
    return (
        <div className='mt-32 lg:mt-0 lg:min-h-screen flex items-center justify-center'>
            <AdminLoginForm />
        </div>
    );
}

//userlogin
export default function Page() {
    return (
        <div className='w-full min-h-screen lg:grid-cols-2'>
            <div className='hidden lg:block relative bg muted'>
                <Image src={PlaceholderImage} alt='Image' layout='fill'
                    className='h-full w-full object-cover dark:brightness-[0.2] dark:grayscale'
                    />
                <div className='absolute w-full h-screen bg-foreground/50 p-12 flex flex-col justify-between'>
                    <div>
                    <h1 className='text-white text-4xl font-semibold'>PENDEKAR</h1>
                    <p className='text-white text-lg'>Pelayanan Desa Karyalaksana</p>
                </div>
                <div><p className='text-white text-sm'>@ 2024 Desa Karyalaksana.</p></div>
            </div>
        </div>
        <div className='flex items-center justify-center py-12'>
            <div className='mx-auto grid w-[350px] gap-6'><UserLoginForm /></div>
        </div>
    </div>
    );
}

//userdashboard
export default async function Page() {
    const session = await auth();
    const nik = session?.user.nik;
    return (
        <>
            <div className='grid gap-4 md:grid-cols-2 lg:grid-cols-4'>
                <Suspense fallback={<AdminDashboardCardsSkeleton />}>
                    <UserDashboardCards nik={nik!} />
                </Suspense>
            </div>
            <div className='grid gap-4'>
                <Suspense fallback={<RecentTableSkeleton />}>
                    <RecentUserPermohonan nik={nik!} />
                </Suspense>
            </div>
        </>
    );
}

//User Mengajukan Surat
export default function Page(){
    return (
        <div className='w-full min-h-full flex flex-col gap-y-4'>
            <div className='flex justify-between'>
                <h1 className='text-xl md:text-2xl font-semibold'>
                    Ajukan Permohonan Surat Baru                
                </h1>
            </div>
            <div className='rounded-sm grid md:grid-cols-3 gap-4'>
                <div className='grid gap-4'>
                    <JenisSuratCard path='/user/ajukan/sktm'
                     title='Surat Keterangan Tidak Mampu' description='Ajukan Surat' />
                    <JenisSuratCard path='/user/ajukan/skbn'
                     title='Surat Keterangan Beda Nama' description='Ajukan Surat' />
                </div>
                <div className='grid gap-4'>
                    <JenisSuratCard path='/user/ajukan/skklhr'
                     title='Surat Keterangan Kelahiran' description='Ajukan Surat' />
                    <JenisSuratCard path='/user/ajukan/skkmtn'
                     title='Surat Keterangan Kematian' description='Ajukan Surat' />
                </div>
                <div className='grip gap-4'>
                    <JenisSuratCard path='/user/ajukan/sku'
                     title='Surat Keterangan Usaha' description='Ajukan Surat' />
                    <JenisSuratCard path='/user/ajukan/sik'
                     titile='Surat Izin Keramaian' description='Ajukan Surat' />
                </div>
            </div>
        </div>
    );   
}
