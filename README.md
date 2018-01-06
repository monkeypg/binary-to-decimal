# binary-to-decimal
- 很經典的題目類型(以前計概常考)，看如何用collect來實作

## 寫法一
```php
function binaryToDecimal($binary)
{
    $total = 0;
    $exponent = strlen($binary) - 1;
    for ($i = 0; $i < strlen($binary); $i++) {
        $decimal = $binary[$i] * (2 ** $exponent);
        $total += $decimal;
        $exponent--;
    }
    return $total;
}
echo binaryToDecimal("100110101");
```

## 寫法二
```php
//寫法二
//跑程式時要注意要把其中一個fun註解掉，不然會撞名
function binaryToDecimal($binary)
{
    return collect(str_split($binary))
        ->reverse()
        ->values()
        ->map(function ($column, $exponent) {
            return $column * (2 ** $exponent);
        })->sum();
}

echo binaryToDecimal("100110101");
```

