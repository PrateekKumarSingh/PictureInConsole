#[enum]::GetValues([System.ConsoleColor])
$Colors = @{
            'FF000000' =   'Black'         
            'FF000080' =   'DarkBlue'      
            'FF008000' =   'DarkGreen'     
            'FF008080' =   'DarkCyan'      
            'FF800000' =   'DarkRed'       
            'FF800080' =   'DarkMagenta'   
            'FF808000' =   'DarkYellow'    
            'FFC0C0C0' =   'Gray'          
            'FF808080' =   'DarkGray'      
            'FF0000FF' =   'Blue'          
            'FF00FF00' =   'Green'         
            'FF00FFFF' =   'Cyan'          
            'FFFF0000' =   'Red'           
            'FFFF00FF' =   'Magenta'       
            'FFFFFF00' =   'Yellow'         
            'FFFFFFFF' =   'White'         
}

$BitMap = [System.Drawing.Bitmap]::FromFile("C:\Users\prateesi\Desktop\colors.png")
#$BitMap.Height%100

Function Get-ClosetConsoleColor($PixelColor)
{
    $Differences = Foreach($item in $Colors.Keys)
    {
        ''|select @{n='Color';e={$Item}},@{n='Diff';e={[math]::abs([convert]::ToInt32($Item,16) - [convert]::ToInt32($PixelColor,16))}} 
    }

    ($Differences |sort Diff)[0].color
}


Foreach($y in (1..($BitMap.Height-1)))
{
    Foreach($x in (1..($BitMap.Width-1)))
    {
        #'' | select @{n='X';e={$X}},@{n='Y';e={$Y}}, @{n='Color';e={($BitMap.GetPixel($X,$Y)).name}} | export-csv C:\Temp\bitmap.csv -NoTypeInformation -Append
        #
        #"$x,$y"
        
        $Pixel = $BitMap.GetPixel($X,$Y)
        
        $BackGround = $Colors.Item((Get-ClosetConsoleColor $Pixel.name))

            Write-Host " " -NoNewline -BackgroundColor $BackGround
    }

    Write-Host ""
}





