# -*- coding: utf-8 -*-
import vk_api


def main():
    token='4169ac9a7a64c93d7b45c9906edb4a9d1aca590792dd840965a6fb8810532b1c82b7c198edc5f4e03cfbe'
    vk_session = vk_api.VkApi(token=token)

    try:
        vk_session.auth(token_only=True)
    except vk_api.AuthError as error_msg:
        print(error_msg)
        return

    upload = vk_api.VkUpload(vk_session)

    photo = upload.photo(  # Подставьте свои данные
        '/root/3301.jpg',
        album_id=200851098,
        group_id=74030368
    )

    vk_photo_url = 'https://vk.com/photo{}_{}'.format(
        photo[0]['owner_id'], photo[0]['id']
    )

    print(photo, '\nLink: ', vk_photo_url)


if __name__ == '__main__':
    main()
