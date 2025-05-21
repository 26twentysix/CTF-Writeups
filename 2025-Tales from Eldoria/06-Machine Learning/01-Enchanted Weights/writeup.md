# Enchanted Weights

![img_29.png](task%2Fimg_29.png)

Гуляем по тензорам, получаем флаг
```python
import torch

FILE_PATH = "eldorian_artifact.pth"

checkpoint = torch.load(FILE_PATH, map_location="cpu")
for key, tensor in checkpoint.items():
    if isinstance(tensor, torch.Tensor):
        array = tensor.detach().cpu().numpy()
        flag_numbers = "".join([chr(int(x)) for x in array.flatten() if 32 <= x <= 126])
        print(flag_numbers)
```
HTB{Cry5t4l_RuN3s_0f_Eld0r1a}
