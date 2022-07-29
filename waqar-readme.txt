COMMAND

IMAGE SIZE 224
python main.py --epochs 300 \
                --model convnext_tiny \
                --data_set image_folder \
                --data_path ../CIFAR-10-images/train \
                --eval_data_path ../CIFAR-10-images/test \
                --nb_classes 10 \
                --num_workers 8 \
                --warmup_epochs 0 \
                --save_ckpt true \
                --output_dir model_ckpt \
                --finetune convnext_tiny_22k_224.pth \
                --cutmix 0 \
                --mixup 0 --lr 4e-4 \
                --input_size 224 \
                --batch_size 64 \
                --enable_wandb true --wandb_ckpt true
            
EVALUATION    
python main.py --epochs 100 \
                --model convnext_tiny \
                --data_set image_folder \
                --data_path ../CIFAR-10-images/train \
                --eval_data_path ../CIFAR-10-images/test \
                --nb_classes 10 \
                --num_workers 8 \
                --warmup_epochs 0 \
                --save_ckpt true \
                --output_dir model_ckpt \
                --finetune ./model_ckpt/checkpoint-best.pth \
                --cutmix 0 \
                --mixup 0 --lr 4e-4 \
                --enable_wandb true --wandb_ckpt true \
                --eval true
                
IMAGE SIZE 384
python main.py --epochs 400 \
                --model convnext_tiny \
                --data_set image_folder \
                --data_path ../CIFAR-10-images/train \
                --eval_data_path ../CIFAR-10-images/test \
                --nb_classes 10 \
                --num_workers 8 \
                --warmup_epochs 0 \
                --save_ckpt true \
                --output_dir model_ckpt \
                --finetune convnext_tiny_22k_1k_384.pth  \
                --cutmix 0 \
                --mixup 0 --lr 4e-4 \
                --input_size 384 \
                --batch_size 16 \
                --enable_wandb true --wandb_ckpt true
